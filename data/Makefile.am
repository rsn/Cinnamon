desktopdir=$(datadir)/applications
desktop_DATA = cinnamon.desktop

# We substitute in bindir so it works as an autostart
# file when built in a non-system prefix
%.desktop.in:%.desktop.in.in
	$(AM_V_GEN) sed -e "s|@bindir[@]|$(bindir)|" \
	    -e "s|@VERSION[@]|$(VERSION)|" \
	    $< > $@ || rm $@

# Placeholder until we add intltool
%.desktop:%.desktop.in
	$(AM_V_GEN) sed s/^_// < $< > $@ || rm $@

searchprovidersdir = $(pkgdatadir)/search_providers
dist_searchproviders_DATA =				\
	search_providers/google.xml				\
	search_providers/wikipedia.xml

themedir = $(pkgdatadir)/theme
dist_theme_DATA = \
	theme/add-workspace.png			\
	theme/add-workspace-hover.png		\
	theme/calendar-arrow-left.svg		\
	theme/calendar-arrow-right.svg		\
	theme/calendar-today.svg		\
	theme/close-window.svg			\
	theme/close.svg				\
	theme/corner-ripple.png			\
	theme/dash-placeholder.svg		\
	theme/filter-selected-ltr.svg		\
	theme/filter-selected-rtl.svg		\
	theme/gdm.css				\
	theme/cinnamon.css			\
	theme/menu.png				\
	theme/overview.png			\
	theme/overview-hover.png		\
	theme/panel-border.svg			\
	theme/panel-button-border.svg		\
	theme/panel-button-highlight-narrow.svg	\
	theme/panel-button-highlight-wide.svg	\
	theme/process-working.svg		\
	theme/running-indicator.svg		\
	theme/scroll-hhandle.svg		\
	theme/scroll-vhandle.svg		\
	theme/source-button-border.svg		\
	theme/thumbnail.png			\
	theme/thumbnail-generic.png		\
	theme/toggle-off-us.svg			\
	theme/toggle-off-intl.svg		\
	theme/toggle-on-us.svg			\
	theme/toggle-on-intl.svg		\
	theme/trash-icon.png			\
	theme/ws-switch-arrow-up.svg		\
	theme/ws-switch-arrow-down.svg		\
	theme/player-paused.svg		\
	theme/player-playing.svg		\
	theme/player-stopped.svg

gsettings_SCHEMAS = org.cinnamon.gschema.xml

@INTLTOOL_XML_NOMERGE_RULE@
@GSETTINGS_RULES@

# We need to compile schemas at make time
# to run from source tree
gschemas.compiled: $(gsettings_SCHEMAS:.xml=.valid)
	$(AM_V_GEN) $(GLIB_COMPILE_SCHEMAS) --targetdir=. .

all-local: gschemas.compiled


shadersdir = $(pkgdatadir)/shaders
shaders_DATA = \
	shaders/dim-window.glsl


EXTRA_DIST =						\
	cinnamon.desktop.in.in			\
	$(menu_DATA)					\
	$(shaders_DATA)					\
	org.cinnamon.gschema.xml.in

CLEANFILES =						\
	cinnamon.desktop.in				\
	$(desktop_DATA)					\
	$(gsettings_SCHEMAS)				\
	gschemas.compiled

