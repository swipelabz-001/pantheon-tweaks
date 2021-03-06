project('pantheon-tweaks', 'vala', 'c', version: '1.0')

switchboard_dep = dependency('switchboard-2.0')
gettext_name = meson.project_name() + '-plug'
pkgdatadir = join_paths(switchboard_dep.get_pkgconfig_variable('plugsdir'), 'personal')

i18n = import('i18n')

add_global_arguments(
    '-DGETTEXT_PACKAGE="@0@"'.format(gettext_name),
    language:'c'
)

subdir('icon')
subdir('po')

plug_files = files(
    'src/Tweaks.vala',
    'src/Settings/GtkSettings.vala',
    'src/Settings/ThemeSettings.vala',
    'src/Settings/XSettings.vala',
    'src/Panes/AudiencePane.vala',
    'src/Panes/AnimationsPane.vala',
    'src/Panes/AppearancePane.vala',
    'src/Panes/FontsPane.vala',
    'src/Panes/MiscPane.vala',
    'src/Panes/FilesPane.vala',
    'src/Panes/TerminalPane.vala',
    'src/Widgets/Categories.vala',
)

shared_module(
    meson.project_name(),
    plug_files,
    dependencies: [
        dependency('gee-0.8'),
        dependency('glib-2.0'),
        dependency('granite'),
        dependency('gtk+-3.0'),
        meson.get_compiler('vala').find_library('posix'),
        switchboard_dep
    ],
    install: true,
    install_dir: pkgdatadir
)

meson.add_install_script('meson/post_install.py')
