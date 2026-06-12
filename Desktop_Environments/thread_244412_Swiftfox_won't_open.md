---
title: "Swiftfox won't open"
date: 2006-08-26
forum: Desktop Environments
---

### Post by bradcarr on 2006-08-26
First post - new to ubuntu 

I recently install swiftfox and when I go to open it
I get failed to execute child process "opt/swiftfox/swiftfox" (No such file or directory)
Tried changing the path with no luck.
any help is greatly appreciated

THANKS

---

### Post by meng on 2006-08-26
Try
locate swiftfox
(I wonder if that should be /opt/swiftfox/swiftfox)

---

### Post by bradcarr on 2006-08-26
/opt/swiftfox/swiftfox

doesn't work either

thanks for the reply !

---

### Post by meng on 2006-08-26
Okay, according to the getswiftfox website, you should try
/usr/lib/swiftfox
but if you get an output from the command
locate swiftofx
that would be the definitive answer.

---

### Post by bradcarr on 2006-08-26
tried /usr/lib/swiftfox with no luck 

not quiet sure by what you mean "but if you get an output from the command
locate swiftofx"

but I typed "locate swiftofx" in a terminal it just went back to a prompt

---

### Post by meng on 2006-08-26
Sorry I meant
locate swiftfox
not
locate swiftofx

this command tells you where the file/s named swiftfox are located.

---

### Post by bradcarr on 2006-08-26
typed "locate swiftfox" in a terminal 

came back with a lot of output

So Im guessing that I use one of the outputs for the path

If that is the case not quiet sure which one to use

---

### Post by ash211 on 2006-08-26
Yes, it's one of those.  Post the output of "locate swiftfox" and we can tell you which to use.

---

### Post by bradcarr on 2006-08-26
/home/bcarter/DOWNLOADS/swiftfox-1.5.0.6-athlon-xp.tar.bz2
/home/bcarter/swiftfox
/home/bcarter/swiftfox/res
/home/bcarter/swiftfox/res/dtd
/home/bcarter/swiftfox/res/dtd/xhtml11.dtd
/home/bcarter/swiftfox/res/dtd/mathml.dtd
/home/bcarter/swiftfox/res/table-add-column-after.gif
/home/bcarter/swiftfox/res/html
/home/bcarter/swiftfox/res/html/gopher-menu.gif
/home/bcarter/swiftfox/res/html/gopher-audio.gif
/home/bcarter/swiftfox/res/html/gopher-telnet.gif
/home/bcarter/swiftfox/res/html/gopher-sound.gif
/home/bcarter/swiftfox/res/html/gopher-image.gif
/home/bcarter/swiftfox/res/html/gopher-unknown.gif
/home/bcarter/swiftfox/res/html/gopher-binary.gif
/home/bcarter/swiftfox/res/html/gopher-find.gif
/home/bcarter/swiftfox/res/html/gopher-text.gif
/home/bcarter/swiftfox/res/html/gopher-movie.gif
/home/bcarter/swiftfox/res/viewer.properties
/home/bcarter/swiftfox/res/cmessage.txt
/home/bcarter/swiftfox/res/table-remove-row-hover.gif
/home/bcarter/swiftfox/res/fonts
/home/bcarter/swiftfox/res/fonts/mathfontPUA.properties
/home/bcarter/swiftfox/res/fonts/fontEncoding.properties
/home/bcarter/swiftfox/res/fonts/pangoFontEncoding.properties
/home/bcarter/swiftfox/res/fonts/mathfontMath1.properties
/home/bcarter/swiftfox/res/fonts/mathfontMath2.properties
/home/bcarter/swiftfox/res/fonts/mathfontMTExtra.properties
/home/bcarter/swiftfox/res/fonts/mathfontSymbol.properties
/home/bcarter/swiftfox/res/fonts/mathfontCMSY10.properties
/home/bcarter/swiftfox/res/fonts/mathfont.properties
/home/bcarter/swiftfox/res/fonts/mathfontMath4.properties
/home/bcarter/swiftfox/res/fonts/mathfontCMEX10.properties
/home/bcarter/swiftfox/res/table-add-row-before-hover.gif
/home/bcarter/swiftfox/res/charsetData.properties
/home/bcarter/swiftfox/res/broken-image.gif
/home/bcarter/swiftfox/res/table-add-row-after.gif
/home/bcarter/swiftfox/res/table-add-column-after-hover.gif
/home/bcarter/swiftfox/res/html.css
/home/bcarter/swiftfox/res/table-remove-column-active.gif
/home/bcarter/swiftfox/res/table-remove-column.gif
/home/bcarter/swiftfox/res/charsetalias.properties
/home/bcarter/swiftfox/res/EditorOverride.css
/home/bcarter/swiftfox/res/table-remove-column-hover.gif
/home/bcarter/swiftfox/res/table-add-row-after-active.gif
/home/bcarter/swiftfox/res/sample.unixpsfonts.properties
/home/bcarter/swiftfox/res/quirk.css
/home/bcarter/swiftfox/res/svg.css
/home/bcarter/swiftfox/res/language.properties
/home/bcarter/swiftfox/res/table-add-row-before-active.gif
/home/bcarter/swiftfox/res/table-add-column-before-active.gif
/home/bcarter/swiftfox/res/table-add-row-after-hover.gif
/home/bcarter/swiftfox/res/langGroups.properties
/home/bcarter/swiftfox/res/forms.css
/home/bcarter/swiftfox/res/grabber.gif
/home/bcarter/swiftfox/res/table-add-row-before.gif
/home/bcarter/swiftfox/res/unixcharset.properties
/home/bcarter/swiftfox/res/ua.css
/home/bcarter/swiftfox/res/table-add-column-before-hover.gif
/home/bcarter/swiftfox/res/arrow.gif
/home/bcarter/swiftfox/res/arrowd.gif
/home/bcarter/swiftfox/res/bloatcycle.html
/home/bcarter/swiftfox/res/table-add-column-before.gif
/home/bcarter/swiftfox/res/table-remove-row-active.gif
/home/bcarter/swiftfox/res/hiddenWindow.html
/home/bcarter/swiftfox/res/table-remove-row.gif
/home/bcarter/swiftfox/res/table-add-column-after-active.gif
/home/bcarter/swiftfox/res/loading-image.gif
/home/bcarter/swiftfox/res/entityTables
/home/bcarter/swiftfox/res/entityTables/html40Special.properties
/home/bcarter/swiftfox/res/entityTables/html40Symbols.properties
/home/bcarter/swiftfox/res/entityTables/mathml20.properties
/home/bcarter/swiftfox/res/entityTables/htmlEntityVersions.properties
/home/bcarter/swiftfox/res/entityTables/transliterate.properties
/home/bcarter/swiftfox/res/entityTables/html40Latin1.properties
/home/bcarter/swiftfox/res/viewsource.css
/home/bcarter/swiftfox/res/mathml.css
/home/bcarter/swiftfox/xpicleanup
/home/bcarter/swiftfox/regxpcom
/home/bcarter/swiftfox/updater.ini
/home/bcarter/swiftfox/searchplugins
/home/bcarter/swiftfox/searchplugins/google.gif
/home/bcarter/swiftfox/searchplugins/google.src
/home/bcarter/swiftfox/searchplugins/amazondotcom.png
/home/bcarter/swiftfox/searchplugins/amazondotcom.src
/home/bcarter/swiftfox/searchplugins/answers.png
/home/bcarter/swiftfox/searchplugins/answers.src
/home/bcarter/swiftfox/searchplugins/yahoo.gif
/home/bcarter/swiftfox/searchplugins/yahoo.src
/home/bcarter/swiftfox/searchplugins/creativecommons.png
/home/bcarter/swiftfox/searchplugins/creativecommons.src
/home/bcarter/swiftfox/searchplugins/eBay.gif
/home/bcarter/swiftfox/searchplugins/eBay.src
/home/bcarter/swiftfox/libssl3.so
/home/bcarter/swiftfox/LICENSE
/home/bcarter/swiftfox/xpcshell
/home/bcarter/swiftfox/icons
/home/bcarter/swiftfox/icons/icon32.png
/home/bcarter/swiftfox/icons/icon48.png
/home/bcarter/swiftfox/icons/mozicon128.png
/home/bcarter/swiftfox/icons/document.png
/home/bcarter/swiftfox/icons/mozicon16.xpm
/home/bcarter/swiftfox/icons/mozicon50.xpm
/home/bcarter/swiftfox/xpidl
/home/bcarter/swiftfox/dependentlibs.list
/home/bcarter/swiftfox/greprefs
/home/bcarter/swiftfox/greprefs/security-prefs.js
/home/bcarter/swiftfox/greprefs/all.js
/home/bcarter/swiftfox/greprefs/xpinstall.js
/home/bcarter/swiftfox/swiftfox
/home/bcarter/swiftfox/run-mozilla.sh
/home/bcarter/swiftfox/libmozjs.so
/home/bcarter/swiftfox/xpt_dump
/home/bcarter/swiftfox/xpt_link
/home/bcarter/swiftfox/libnspr4.so
/home/bcarter/swiftfox/libsoftokn3.so
/home/bcarter/swiftfox/components
/home/bcarter/swiftfox/components/dom_base.xpt
/home/bcarter/swiftfox/components/layout_printing.xpt
/home/bcarter/swiftfox/components/passwordmgr.xpt
/home/bcarter/swiftfox/components/mozbrwsr.xpt
/home/bcarter/swiftfox/components/appstartup.xpt
/home/bcarter/swiftfox/components/mozfind.xpt
/home/bcarter/swiftfox/components/nsKillAll.js
/home/bcarter/swiftfox/components/nsSetDefaultBrowser.js
/home/bcarter/swiftfox/components/chardet.xpt
/home/bcarter/swiftfox/components/nsProxyAutoConfig.js
/home/bcarter/swiftfox/components/imglib2.xpt
/home/bcarter/swiftfox/components/htmlparser.xpt
/home/bcarter/swiftfox/components/dom_stylesheets.xpt
/home/bcarter/swiftfox/components/windowwatcher.xpt
/home/bcarter/swiftfox/components/nsSchemaValidatorRegexp.js
/home/bcarter/swiftfox/components/rdf.xpt
/home/bcarter/swiftfox/components/libjsd.so
/home/bcarter/swiftfox/components/xpcom_xpti.xpt
/home/bcarter/swiftfox/components/dom_canvas.xpt
/home/bcarter/swiftfox/components/fastfind.xpt
/home/bcarter/swiftfox/components/update.xpt
/home/bcarter/swiftfox/components/xpinstall.xpt
/home/bcarter/swiftfox/components/mozgnome.xpt
/home/bcarter/swiftfox/components/xpcom_ds.xpt
/home/bcarter/swiftfox/components/pippki.xpt
/home/bcarter/swiftfox/components/jsdservice.xpt
/home/bcarter/swiftfox/components/jsconsole-clhandler.js
/home/bcarter/swiftfox/components/necko_res.xpt
/home/bcarter/swiftfox/components/docshell.xpt
/home/bcarter/swiftfox/components/windowds.xpt
/home/bcarter/swiftfox/components/xpcom_io.xpt
/home/bcarter/swiftfox/components/accessibility-atk.xpt
/home/bcarter/swiftfox/components/dom.xpt
/home/bcarter/swiftfox/components/directory.xpt
/home/bcarter/swiftfox/components/dom_svg.xpt
/home/bcarter/swiftfox/components/toolkitprofile.xpt
/home/bcarter/swiftfox/components/widget.xpt
/home/bcarter/swiftfox/components/exthandler.xpt
/home/bcarter/swiftfox/components/necko_dns.xpt
/home/bcarter/swiftfox/components/content_html.xpt
/home/bcarter/swiftfox/components/shellservice.xpt
/home/bcarter/swiftfox/components/nsFilePicker.js
/home/bcarter/swiftfox/components/nsUpdateService.js
/home/bcarter/swiftfox/components/libimgicon.so
/home/bcarter/swiftfox/components/progressDlg.xpt
/home/bcarter/swiftfox/components/nsDictionary.js
/home/bcarter/swiftfox/components/history.xpt
/home/bcarter/swiftfox/components/layout_base.xpt
/home/bcarter/swiftfox/components/dom_html.xpt
/home/bcarter/swiftfox/components/chrome.xpt
/home/bcarter/swiftfox/components/necko_viewsource.xpt
/home/bcarter/swiftfox/components/dom_events.xpt
/home/bcarter/swiftfox/components/webbrowserpersist.xpt
/home/bcarter/swiftfox/components/prefetch.xpt
/home/bcarter/swiftfox/components/content_htmldoc.xpt
/home/bcarter/swiftfox/components/txmgr.xpt
/home/bcarter/swiftfox/components/nsHelperAppDlg.js
/home/bcarter/swiftfox/components/xml-rpc.xpt
/home/bcarter/swiftfox/components/dom_xpath.xpt
/home/bcarter/swiftfox/components/satchel.xpt
/home/bcarter/swiftfox/components/gksvgrenderer.xpt
/home/bcarter/swiftfox/components/toolkitremote.xpt
/home/bcarter/swiftfox/components/autocomplete.xpt
/home/bcarter/swiftfox/components/bookmarks.xpt
/home/bcarter/swiftfox/components/embed_base.xpt
/home/bcarter/swiftfox/components/jsconsole.xpt
/home/bcarter/swiftfox/components/necko_about.xpt
/home/bcarter/swiftfox/components/find.xpt
/home/bcarter/swiftfox/components/necko_socket.xpt
/home/bcarter/swiftfox/components/locale.xpt
/home/bcarter/swiftfox/components/mimetype.xpt
/home/bcarter/swiftfox/components/xulapp.xpt
/home/bcarter/swiftfox/components/commandlines.xpt
/home/bcarter/swiftfox/components/pipboot.xpt
/home/bcarter/swiftfox/components/shistory.xpt
/home/bcarter/swiftfox/components/sidebar.xpt
/home/bcarter/swiftfox/components/nsBrowserContentHandler.js
/home/bcarter/swiftfox/components/layout_xul_tree.xpt
/home/bcarter/swiftfox/components/plugin.xpt
/home/bcarter/swiftfox/components/schemavalidation.xpt
/home/bcarter/swiftfox/components/xmlextras.xpt
/home/bcarter/swiftfox/components/caps.xpt
/home/bcarter/swiftfox/components/commandhandler.xpt
/home/bcarter/swiftfox/components/gfx.xpt
/home/bcarter/swiftfox/components/nsXmlRpcClient.js
/home/bcarter/swiftfox/components/browsercompsbase.xpt
/home/bcarter/swiftfox/components/necko_data.xpt
/home/bcarter/swiftfox/components/necko_cookie.xpt
/home/bcarter/swiftfox/components/webshell_idls.xpt
/home/bcarter/swiftfox/components/profile.xpt
/home/bcarter/swiftfox/components/websrvcs.xpt
/home/bcarter/swiftfox/components/xpcom_components.xpt
/home/bcarter/swiftfox/components/libmozgnome.so
/home/bcarter/swiftfox/components/dom_views.xpt
/home/bcarter/swiftfox/components/necko_ftp.xpt
/home/bcarter/swiftfox/components/nsCloseAllWindows.js
/home/bcarter/swiftfox/components/xultmpl.xpt
/home/bcarter/swiftfox/components/downloads.xpt
/home/bcarter/swiftfox/components/nsBrowserGlue.js
/home/bcarter/swiftfox/components/dom_range.xpt
/home/bcarter/swiftfox/components/accessibility.xpt
/home/bcarter/swiftfox/components/uriloader.xpt
/home/bcarter/swiftfox/components/lwbrk.xpt
/home/bcarter/swiftfox/components/dom_core.xpt
/home/bcarter/swiftfox/components/imgicon.xpt
/home/bcarter/swiftfox/components/xpcom_base.xpt
/home/bcarter/swiftfox/components/uconv.xpt
/home/bcarter/swiftfox/components/pref.xpt
/home/bcarter/swiftfox/components/dom_xbl.xpt
/home/bcarter/swiftfox/components/txtsvc.xpt
/home/bcarter/swiftfox/components/unicharutil.xpt
/home/bcarter/swiftfox/components/extensions.xpt
/home/bcarter/swiftfox/components/search.xpt
/home/bcarter/swiftfox/components/oji.xpt
/home/bcarter/swiftfox/components/migration.xpt
/home/bcarter/swiftfox/components/necko_http.xpt
/home/bcarter/swiftfox/components/appshell.xpt
/home/bcarter/swiftfox/components/content_xslt.xpt
/home/bcarter/swiftfox/components/nsInterfaceInfoToIDL.js
/home/bcarter/swiftfox/components/nsSidebar.js
/home/bcarter/swiftfox/components/cookie.xpt
/home/bcarter/swiftfox/components/alerts.xpt
/home/bcarter/swiftfox/components/xpcom_obsolete.xpt
/home/bcarter/swiftfox/components/nsDefaultCLH.js
/home/bcarter/swiftfox/components/xpconnect.xpt
/home/bcarter/swiftfox/components/necko_file.xpt
/home/bcarter/swiftfox/components/webBrowser_core.xpt
/home/bcarter/swiftfox/components/proxyObjInst.xpt
/home/bcarter/swiftfox/components/editor.xpt
/home/bcarter/swiftfox/components/xuldoc.xpt
/home/bcarter/swiftfox/components/libnkgnomevfs.so
/home/bcarter/swiftfox/components/dom_css.xpt
/home/bcarter/swiftfox/components/content_xmldoc.xpt
/home/bcarter/swiftfox/components/dom_traversal.xpt
/home/bcarter/swiftfox/components/nsResetPref.js
/home/bcarter/swiftfox/components/autoconfig.xpt
/home/bcarter/swiftfox/components/xpcom_threads.xpt
/home/bcarter/swiftfox/components/nsProgressDialog.js
/home/bcarter/swiftfox/components/jar.xpt
/home/bcarter/swiftfox/components/dom_loadsave.xpt
/home/bcarter/swiftfox/components/dom_xul.xpt
/home/bcarter/swiftfox/components/nsExtensionManager.js
/home/bcarter/swiftfox/components/pipnss.xpt
/home/bcarter/swiftfox/components/libschemavalidation.so
/home/bcarter/swiftfox/components/layout_xul.xpt
/home/bcarter/swiftfox/components/content_base.xpt
/home/bcarter/swiftfox/components/composer.xpt
/home/bcarter/swiftfox/components/libxpinstall.so
/home/bcarter/swiftfox/components/necko.xpt
/home/bcarter/swiftfox/components/necko_strconv.xpt
/home/bcarter/swiftfox/components/content_xtf.xpt
/home/bcarter/swiftfox/components/filepicker.xpt
/home/bcarter/swiftfox/components/necko_cache.xpt
/home/bcarter/swiftfox/components/intl.xpt
/home/bcarter/swiftfox/libnss3.so
/home/bcarter/swiftfox/firefox
/home/bcarter/swiftfox/libplds4.so
/home/bcarter/swiftfox/chrome
/home/bcarter/swiftfox/chrome/reporter.manifest
/home/bcarter/swiftfox/chrome/en-US.jar
/home/bcarter/swiftfox/chrome/pippki.jar
/home/bcarter/swiftfox/chrome/icons
/home/bcarter/swiftfox/chrome/icons/default
/home/bcarter/swiftfox/chrome/icons/default/default.xpm
/home/bcarter/swiftfox/chrome/chromelist.txt
/home/bcarter/swiftfox/chrome/comm.manifest
/home/bcarter/swiftfox/chrome/browser.manifest
/home/bcarter/swiftfox/chrome/en-US.manifest
/home/bcarter/swiftfox/chrome/pippki.manifest
/home/bcarter/swiftfox/chrome/toolkit.manifest
/home/bcarter/swiftfox/chrome/comm.jar
/home/bcarter/swiftfox/chrome/toolkit.jar
/home/bcarter/swiftfox/chrome/classic.jar
/home/bcarter/swiftfox/chrome/reporter.jar
/home/bcarter/swiftfox/chrome/classic.manifest
/home/bcarter/swiftfox/chrome/browser.jar
/home/bcarter/swiftfox/libnssckbi.so
/home/bcarter/swiftfox/defaults
/home/bcarter/swiftfox/defaults/pref
/home/bcarter/swiftfox/defaults/pref/firefox.js
/home/bcarter/swiftfox/defaults/pref/firefox-l10n.js
/home/bcarter/swiftfox/defaults/pref/channel-prefs.js
/home/bcarter/swiftfox/defaults/pref/reporter.js
/home/bcarter/swiftfox/defaults/autoconfig
/home/bcarter/swiftfox/defaults/autoconfig/platform.js
/home/bcarter/swiftfox/defaults/autoconfig/prefcalls.js
/home/bcarter/swiftfox/defaults/profile
/home/bcarter/swiftfox/defaults/profile/bookmarks.html
/home/bcarter/swiftfox/defaults/profile/mimeTypes.rdf
/home/bcarter/swiftfox/defaults/profile/chrome
/home/bcarter/swiftfox/defaults/profile/chrome/userContent-example.css
/home/bcarter/swiftfox/defaults/profile/chrome/userChrome-example.css
/home/bcarter/swiftfox/defaults/profile/localstore.rdf
/home/bcarter/swiftfox/defaults/profile/prefs.js
/home/bcarter/swiftfox/defaults/profile/search.rdf
/home/bcarter/swiftfox/swiftfox-bin
/home/bcarter/swiftfox/init.d
/home/bcarter/swiftfox/init.d/README
/home/bcarter/swiftfox/libxpcom_core.so
/home/bcarter/swiftfox/libplc4.so
/home/bcarter/swiftfox/README.txt
/home/bcarter/swiftfox/libxpcom_compat.so
/home/bcarter/swiftfox/updater
/home/bcarter/swiftfox/extensions
/home/bcarter/swiftfox/extensions/inspector@mozilla.org
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/chrome.manifest
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/install.rdf
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/components
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/components/inspector-cmd line.js
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/components/inspector.xpt
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/components/libinspector. so
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/chrome
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/chrome/inspector.jar
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/chrome/chromelist.txt
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/defaults
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/defaults/preferences
/home/bcarter/swiftfox/extensions/inspector@mozilla.org/defaults/preferences/ins pector.js
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/chrome. manifest
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/install .rdf
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/compone nts
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/compone nts/xforms.xpt
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/compone nts/nsSchemaValidatorRegexp.js
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/compone nts/schemavalidation.xpt
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/compone nts/libxforms.so
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/compone nts/libschemavalidation.so
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/install .js
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/chrome
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/chrome/ xforms.jar
/home/bcarter/swiftfox/extensions/{cf2812dc-6a7c-4402-b639-4d277dac4c36}/chrome/ chromelist.txt
/home/bcarter/swiftfox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/home/bcarter/swiftfox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install .rdf
/home/bcarter/swiftfox/libxpistub.so
/home/bcarter/swiftfox/libxpcom.so
/home/bcarter/swiftfox/browserconfig.properties
/home/bcarter/swiftfox/firefox-bin
/home/bcarter/swiftfox/libsoftokn3.chk
/home/bcarter/swiftfox/mozilla-xremote-client
/home/bcarter/swiftfox/plugins
/home/bcarter/swiftfox/plugins/libnullplugin.so
/home/bcarter/swiftfox/plugins/libunixprintplugin.so
/home/bcarter/swiftfox/libsmime3.so
/usr/share/applications/swiftfox.desktop
/usr/share/automatix/conf/swiftfox.desktop
/usr/share/automatix/conf/swiftfoxversion

---

### Post by meng on 2006-08-26
It's /home/bcarter/swiftfox/swiftfox

I should have advised you instead of
locate swiftfox
to use
whereis swiftfox

---

### Post by bradcarr on 2006-08-26
IT WORKS !!!!!!!!!!!!!!

SUPER-THANKS guys for the help.

---

