---
title: "How to change icon in kickoff menu"
date: 2012-06-02
forum: Desktop Environments
---

### Post by ztMAMOHT on 2012-06-02
I have install Faenza icon theme, but icon for Leave -> Restart display incorrect. Question: "How to change this icon and for future any other icon in icon pack in KDE".

---

### Post by SeijiSensei on 2012-06-02
Right-click on the launcher button and pick Edit Applications to run kmenuedit.  You can pick the icon for all the menu entries.

---

### Post by whatthefunk on 2012-06-02
> **SeijiSensei said:**
> Right-click on the launcher button and pick Edit Applications to run kmenuedit.  You can pick the icon for all the menu entries.

Thats what I thought too, but it doesnt seem like you can edit items from the "Leave" menu tab through this program.

It looks like youll have to do it manually by editing the .desktop file for Restart.  Not sure which file this is though....  Probably somewhere in /usr/share/kde4/services

---

### Post by ztMAMOHT on 2012-06-03
> **whatthefunk said:**
> Thats what I thought too, but it doesnt seem like you can edit items from the "Leave" menu tab through this program.

It looks like youll have to do it manually by editing the .desktop file for Restart.  Not sure which file this is though....  Probably somewhere in /usr/share/kde4/services

Could you be more specific. I using KDE recently.

---

### Post by ztMAMOHT on 2012-06-03
I have examined a folder(/usr/share/kde4/services) and have not found anything useful.

---

### Post by whatthefunk on 2012-06-04
This has got me really curious.  In other DEs Ive used, shutdown and restart had their own .desktop files where icons could be changed.  It looks like KDE doesnt do this...Ive been looking everywhere and cant find any trace of a .desktop file.  Hmmm....

---

### Post by ztMAMOHT on 2012-06-04
```
code-priest@AdeptusComputerus:/usr/share/kde4/services$ ls
about.protocol                                        kerfuffle_clirar.desktop                           plasma-applet-panelspacer-internal.desktop
activitymanager-plugin-dummy.desktop                  kerfuffle_clizip.desktop                           plasma-applet-pastebin.desktop
activitymanager-plugin-globalshortcuts.desktop        kerfuffle_libarchive.desktop                       plasma-applet-paste.desktop
activitymanager-plugin-nepomuk.desktop                kerfuffle_libarchive_readonly.desktop              plasma_applet_plasmaboard.desktop
activitymanager-plugin-slc.desktop                    kerfuffle_libbz2.desktop                           plasma-applet-playwolf.desktop
aim.protocol                                          kerfuffle_libgz.desktop                            plasma-applet-previewer.desktop
akonadi                                               kerfuffle_libxz.desktop                            plasma-applet-qalculate.desktop
akonadicontact_actions.desktop                        keys.desktop                                       plasma-applet-quickaccess.desktop
akonadi.protocol                                      kfilemodule.desktop                                plasma-applet-quicklaunch.desktop
akregator_config_advanced.desktop                     kfontviewpart.desktop                              plasma-applet-rememberthemilk.desktop
akregator_config_appearance.desktop                   kglobalaccel.desktop                               plasma-applet-rssnow.desktop
akregator_config_archive.desktop                      khelpcenter.desktop                                plasma-applet-searchbox.desktop
akregator_config_browser.desktop                      khotkeys.desktop                                   plasma-applet-showdashboard.desktop
akregator_config_general.desktop                      khtmladaptorpart.desktop                           plasma-applet-showdesktop.desktop
akregator_config_sharemicroblog.desktop               khtml_appearance.desktop                           plasma-applet-simplelauncher.desktop
akregator_mk4storage_plugin.desktop                   khtml_behavior.desktop                             plasma-applet-sm_cpu.desktop
akregator_part.desktop                                khtml.desktop                                      plasma-applet-sm_hdd.desktop
akregator_sharemicroblog_plugin.desktop               khtml_filter.desktop                               plasma-applet-sm_hwinfo.desktop
amarok_collection-audiocdcollection.desktop           khtml_general.desktop                              plasma-applet-sm_net.desktop
amarok_collection-daapcollection.desktop              khtmlimage.desktop                                 plasma-applet-sm_ram.desktop
amarok_collection-ipodcollection.desktop              khtml_java_js.desktop                              plasma-applet-sm_temperature.desktop
amarok_collection-mtpcollection.desktop               kjavaappletviewer.desktop                          plasma-applet-spellcheck.desktop
amarok_collection-mysqlecollection.desktop            kmail_config_accounts.desktop                      plasma-applet-systemloadviewer.desktop
amarok_collection-mysqlservercollection.desktop       kmail_config_appearance.desktop                    plasma-applet-system-monitor.desktop
amarok_collection-playdarcollection.desktop           kmail_config_composer.desktop                      plasma-applet-systemtray.desktop
amarok_collection-umscollection.desktop               kmail_config_identity.desktop                      plasma-applet-timer.desktop
amarok_collection-upnpcollection.desktop              kmail_config_misc.desktop                          plasma-applet-trash.desktop
amarok-containment-vertical.desktop                   kmail_config_security.desktop                      plasma-applet-unitconverter.desktop
amarok-context-applet-albums.desktop                  kmanpart.desktop                                   plasma-applet-weather.desktop
amarok-context-applet-currenttrack.desktop            kmixctrl_restore.desktop                           plasma-applet-weatherstation.desktop
amarok-context-applet-info.desktop                    kmultipart.desktop                                 plasma-applet-webbrowser.desktop
amarok-context-applet-labels.desktop                  knote_config_action.desktop                        plasma-applet-webslice.desktop
amarok-context-applet-lyrics.desktop                  knote_config_display.desktop                       plasma-applet-windowlist.desktop
amarok-context-applet-photos.desktop                  knote_config_editor.desktop                        plasma-battery-default.desktop
amarok-context-applet-similarArtists.desktop          knote_config_network.desktop                       plasma-clock-fuzzy.desktop
amarok-context-applet-spectrum-analyzer.desktop       knote_config_style.desktop                         plasma-comic-default.desktop
amarok-context-applet-tabs.desktop                    knotify4.desktop                                   plasma-containmentactions-applauncher.desktop
amarok-context-applet-upcomingEvents.desktop          konsolepart.desktop                                plasma-containmentactions-contextmenu.desktop
amarok-context-applet-videoclip.desktop               kontact                                            plasma-containmentactions-minimalcontextmenu.desktop
amarok-context-applet-wikipedia.desktop               kontactconfig.desktop                              plasma-containmentactions-paste.desktop
amarok-data-engine-current.desktop                    kopete_accountconfig.desktop                       plasma-containmentactions-switchactivity.desktop
amarok-data-engine-info.desktop                       kopete_addbookmarks.desktop                        plasma-containmentactions-switchdesktop.desktop
amarok-data-engine-labels.desktop                     kopete_aim.desktop                                 plasma-containmentactions-switchwindow.desktop
amarok-data-engine-lyrics.desktop                     kopete_appearanceconfig.desktop                    plasma-containment-desktopdashboard.desktop
amarok-data-engine-photos.desktop                     kopete_autoreplace.desktop                         plasma-containment-desktop.desktop
amarok-data-engine-similarArtists.desktop             kopete_avdeviceconfig.desktop                      plasma-containment-netpanel.desktop
amarok-data-engine-spectrum-analyzer.desktop          kopete_behaviorconfig.desktop                      plasma-containment-newspaper.desktop
amarok-data-engine-tabs.desktop                       kopete_bonjour.desktop                             plasma-containment-panel.desktop
amarok-data-engine-upcomingEvents.desktop             kopete_chatwindowconfig.desktop                    plasma-containment-sal.desktop
amarok-data-engine-videoclip.desktop                  kopete_contactnotes.desktop                        plasma-containment-saverdesktop.desktop
amarok-data-engine-wikipedia.desktop                  kopete_gadu.desktop                                plasma-dataengine-applicationjobs.desktop
amarok_device_massstorage.desktop                     kopete_groupwise.desktop                           plasma-dataengine-apps.desktop
amarok_device_nfs.desktop                             kopete_highlight.desktop                           plasma-dataengine-calendar.desktop
amarok_device_smb.desktop                             kopete_history.desktop                             plasma-dataengine-comic.desktop
amarokitpc.protocol                                   kopete_icq.desktop                                 plasma-dataengine-devicenotifications.desktop
amaroklastfm.protocol                                 kopete_jabber.desktop                              plasma-dataengine-dict.desktop
amarok.protocol                                       kopete_latex.desktop                               plasma-dataengine-executable.desktop
amarok-scriptengine-applet-simple-javascript.desktop  kopete_meanwhile.desktop                           plasma-dataengine-favicons.desktop
amarok-scriptengine-runner-javascript.desktop         kopete_message_indicator.desktop                   plasma-dataengine-filebrowser.desktop
amarok_service_amazonstore_config.desktop             kopete_nowlistening.desktop                        plasma-dataengine-geolocation.desktop
amarok_service_amazonstore.desktop                    kopete_otr.desktop                                 plasma-dataengine-hotplug.desktop
amarok_service_ampache_config.desktop                 kopete_pipes.desktop                               plasma-dataengine-keystate.desktop
amarok_service_ampache.desktop                        kopete_pluginconfig.desktop                        plasma-dataengine-kimpanel.desktop
amarok_service_gpodder_config.desktop                 kopete_privacy.desktop                             plasma-dataengine-ktorrent.desktop
amarok_service_gpodder.desktop                        kopete_qq.desktop                                  plasma-dataengine-microblog.desktop
amarok_service_jamendo.desktop                        kopete_skype.desktop                               plasma-dataengine-mouse.desktop
amarok_service_lastfm_config.desktop                  kopete_sms.desktop                                 plasma-dataengine-network.desktop
amarok_service_lastfm.desktop                         kopete_statistics.desktop                          plasma-dataengine-notifications.desktop
amarok_service_magnatunestore_config.desktop          kopete_statusconfig.desktop                        plasma-dataengine-nowplaying.desktop
amarok_service_magnatunestore.desktop                 kopete_testbed.desktop                             plasma-dataengine-ocs.desktop
amarok_service_mp3tunes_config.desktop                kopete_texteffect.desktop                          plasma-dataengine-places.desktop
amarok_service_mp3tunes.desktop                       kopete_translator.desktop                          plasma-dataengine-potd.desktop
amarok_service_opmldirectory.desktop                  kopete_urlpicpreview.desktop                       plasma-dataengine-powermanagement.desktop
apodprovider.desktop                                  kopete_webpresence.desktop                         plasma-dataengine-rss.desktop
applications.protocol                                 kopete_wlm.desktop                                 plasma-dataengine-share-addon-imgsusepasteorg.desktop
apt+http.protocol                                     kopete_wp.desktop                                  plasma-dataengine-share-addon-imgur.desktop
apt.protocol                                          kopete_yahoo.desktop                               plasma-dataengine-share-addon-kde.desktop
ark_dndextract.desktop                                korganizer                                         plasma-dataengine-share-addon-pastebincom.desktop
ark_part.desktop                                      korganizer_configcolorsandfonts.desktop            plasma-dataengine-share-addon-pasteopensuseorg.desktop
ar.protocol                                           korganizer_configdesignerfields.desktop            plasma-dataengine-share-addon-pasteubuntucom.desktop
audiocd.desktop                                       korganizer_configfreebusy.desktop                  plasma-dataengine-share-addon-privatepastecom.desktop
audiocd.protocol                                      korganizer_configgroupscheduling.desktop           plasma-dataengine-share-addon-simplestimagehosting.desktop
autostart.desktop                                     korganizer_configmain.desktop                      plasma-dataengine-share-addon-wklej.desktop
bell.desktop                                          korganizer_configplugins.desktop                   plasma-dataengine-share-addon-wstaw.desktop
bluedeviladapters.desktop                             korganizer_configtime.desktop                      plasma-dataengine-share.desktop
bluedevil-audio.desktop                               korganizer_configviews.desktop                     plasma-dataengine-soliddevice.desktop
bluedevildevices.desktop                              korganizer_part.desktop                            plasma-dataengine-systemmonitor.desktop
bluedevil-input.desktop                               krarc.protocol                                     plasma-dataengine-tasks.desktop
bluedevil-network-dun.desktop                         kresources                                         plasma-dataengine-time.desktop
bluedevil-network-panu.desktop                        kresources.desktop                                 plasma-dataengine-weather.desktop
bluedevilsendfile.desktop                             kshorturifilter.desktop                            plasma-dict-default.desktop
bluedeviltransfer.desktop                             kspell_enchant.desktop                             plasma-engine-activities.desktop
bluetooth.protocol                                    kspell_hspell.desktop                              plasma-engine-akonadi.desktop
bookmarks.desktop                                     ksplashthememgr.desktop                            plasma-engine-metadata.desktop
bookmarks.protocol                                    ktbwschedulerplugin.desktop                        plasma-engine-mixer.desktop
bzip2.protocol                                        ktdownloadorderplugin.desktop                      plasma-engine-networkmanagement.desktop
bzip.protocol                                         ktexteditor_acomment.desktop                       plasma-engine-rtm.desktop
cache.desktop                                         ktexteditor_autobrace_config.desktop               plasma-engine-searchlaunch.desktop
callto.protocol                                       ktexteditor_autobrace.desktop                      plasma_engine_statusnotifieritem.desktop
camera.protocol                                       ktexteditor_exporter.desktop                       plasma-fileWatcher-default.desktop
cgi.protocol                                          ktexteditor_hlselection.desktop                    plasma-frame-default.desktop
chatwindow.desktop                                    ktexteditor_iconinserter.desktop                   plasma-geolocation-gps.desktop
clock.desktop                                         ktexteditor_insanehtml_le.desktop                  plasma-geolocation-ip.desktop
colors.desktop                                        ktexteditor_insertfile.desktop                     plasma-kolourpicker-default.desktop
comicbookthumbnail.desktop                            ktexteditor_kdatatool.desktop                      plasma-kpart.desktop
componentchooser.desktop                              ktexteditor_python-encoding.desktop                plasma-layout-org.kde.plasma-desktop.defaultPanel.desktop
cookies.desktop                                       ktimetracker_config_behavior.desktop               plasma-layout-org.kde.plasma-desktop.desktopIcons.desktop
cursortheme.desktop                                   ktimetracker_config_display.desktop                plasma-layout-org.kde.plasma-desktop.findWidgets.desktop
cursorthumbnail.desktop                               ktimetracker_config_storage.desktop                plasma-layout-org.kde.plasma-desktop.photoActivity.desktop
data.protocol                                         ktimetrackerpart.desktop                           plasma-layout-org.kde.plasma-desktop.SaL.desktop
desktop.desktop                                       ktinfowidgetplugin.desktop                         plasma-layout-org.kde.plasma-netbook.defaultPage.desktop
desktoppath.desktop                                   ktipfilterplugin.desktop                           plasma-layout-org.kde.plasma-netbook.defaultPanel.desktop
desktop.protocol                                      ktlogviewerplugin.desktop                          plasma-layout-org.kde.plasma-netbook.defaultSal.desktop
desktoptheme.desktop                                  ktmagnetgeneratorplugin.desktop                    plasma-notes-default.desktop
desktopthumbnail.desktop                              ktmediaplayerplugin.desktop                        plasma-packagestructure-comic.desktop
device_automounter_kcm.desktop                        ktscanfolderplugin.desktop                         plasma-packagestructure-javascript-addon.desktop
deviceinfocategory.desktop                            ktscriptingplugin.desktop                          plasma-packagestructure-share.desktop
devinfo.desktop                                       ktsearchplugin.desktop                             plasma-pager-default.desktop
directorythumbnail.desktop                            ktshutdownplugin.desktop                           plasma.protocol
display.desktop                                       ktstatsplugin.desktop                              plasma-runner-activityrunner.desktop
djvuthumbnail.desktop                                 ktsyndicationplugin.desktop                        plasma-runner-bookmarks.desktop
dma.desktop                                           ktupnpplugin.desktop                               plasma-runner-calculator.desktop
dolphinpart.desktop                                   ktwebinterfaceplugin.desktop                       plasma-runner-kill_config.desktop
dragonplayer_part.desktop                             ktzeroconfplugin.desktop                           plasma-runner-kill.desktop
ebrowsing.desktop                                     kuiserver.desktop                                  plasma-runner-locations.desktop
emailwindow.desktop                                   kuriikwsfilter.desktop                             plasma-runner-nepomuksearch.desktop
emoticons.desktop                                     kurisearchfilter.desktop                           plasma-runner-places.desktop
emoticonstheme_adium.desktop                          kwalletconfig.desktop                              plasma-runner-plasma-desktop.desktop
emoticonstheme_kde.desktop                            kwalletd.desktop                                   plasma-runner-powerdevil.desktop
emoticonstheme_pidgin.desktop                         kwalletmanager_show.desktop                        plasma-runner-services.desktop
emoticonstheme_xmpp.desktop                           kwin                                               plasma-runner-sessions.desktop
epodprovider.desktop                                  kwinactions.desktop                                plasma-runner-shell.desktop
exrthumbnail.desktop                                  kwinadvanced.desktop                               plasma-runner-solid.desktop
feed.protocol                                         kwincompositing.desktop                            plasma-runner-webshortcuts.desktop
filebehavior.desktop                                  kwindecoration.desktop                             plasma-runner-windowedwidgets.desktop
filenamesearch.protocol                               kwinfocus.desktop                                  plasma-runner-windows.desktop
file.protocol                                         kwinmoving.desktop                                 plasma-sal-bookmarks.desktop
filetypes.desktop                                     kwinoptions.desktop                                plasma-sal-contacts.desktop
finger.protocol                                       kwinrules.desktop                                  plasma-sal-development.desktop
fish.protocol                                         kwinscreenedges.desktop                            plasma-sal-education.desktop
fixhosturifilter.desktop                              kwintabbox.desktop                                 plasma-sal-games.desktop
flickrprovider.desktop                                language.desktop                                   plasma-sal-graphics.desktop
floppy.protocol                                       language-selector.desktop                          plasma-sal-internet.desktop
fontinst.desktop                                      ldap.protocol                                      plasma-sal-multimedia.desktop
fonts.desktop                                         ldaps.protocol                                     plasma-sal-office.desktop
fonts.protocol                                        libokularGenerator_comicbook.desktop               plasma-sal-system.desktop
fontthumbnail.desktop                                 libokularGenerator_djvu.desktop                    plasma-sal-utility.desktop
ftp.protocol                                          libokularGenerator_dvi.desktop                     plasma-scriptengine-applet-declarative.desktop
ghelp.protocol                                        libokularGenerator_epub.desktop                    plasma-scriptengine-applet-python.desktop
graphicalinfocategory.desktop                         libokularGenerator_fax.desktop                     plasma-scriptengine-applet-simple-javascript.desktop
gvpart.desktop                                        libokularGenerator_fb.desktop                      plasma-scriptengine-dataengine-javascript.desktop
gzip.protocol                                         libokularGenerator_ghostview.desktop               plasma-scriptengine-dataengine-python.desktop
help.protocol                                         libokularGenerator_kimgio.desktop                  plasma-scriptengine-runner-javascript.desktop
htmlthumbnail.desktop                                 libokularGenerator_ooo.desktop                     plasma-scriptengine-runner-python.desktop
http_cache_cleaner.desktop                            libokularGenerator_plucker.desktop                 plasma-scriptengine-wallpaper-python.desktop
http.protocol                                         libokularGenerator_poppler.desktop                 plasma-tasks-default.desktop
https.protocol                                        libokularGenerator_tiff.desktop                    plasma-toolbox-desktoptoolbox.desktop
icons.desktop                                         libokularGenerator_xps.desktop                     plasma-toolbox-nettoolbox.desktop
imagethumbnail.desktop                                localdomainurifilter.desktop                       plasma-toolbox-paneltoolbox.desktop
imap4.protocol                                        lostfoundcategory.desktop                          plasma-wallpaper-color.desktop
imaps.protocol                                        lzma.protocol                                      plasma-wallpaper-image.desktop
info.protocol                                         magnet.protocol                                    plasma-widget-facebook.desktop
interrupts.desktop                                    man.protocol                                       plasma-wifi-signal-default.desktop
ion-bbcukmet.desktop                                  mbox.protocol                                      pnm.protocol
ion-debianweather.desktop                             metainfo.protocol                                  pop3.protocol
ion-envcan.desktop                                    mms.protocol                                       pop3s.protocol
ion-noaa.desktop                                      mmst.protocol                                      powerdevilactivitiesconfig.desktop
ion-wettercom.desktop                                 mmsu.protocol                                      powerdevilbrightnesscontrolaction.desktop
ioports.desktop                                       mouse.desktop                                      powerdevildimdisplayaction.desktop
iso.protocol                                          nepomukactivitiesservice.desktop                   powerdevildpmsaction.desktop
joystick.desktop                                      nepomukbackupsync.desktop                          powerdevilglobalconfig.desktop
jpegthumbnail.desktop                                 nepomukcalendarfeeder.desktop                      powerdevilhandlebuttoneventsaction.desktop
k3baudiometainforenamerplugin.desktop                 nepomukcontactfeeder.desktop                       powerdevilprofilesconfig.desktop
k3baudioprojectcddbplugin.desktop                     nepomukfileindexer.desktop                         powerdevilrunscriptaction.desktop
k3bexternalencoder.desktop                            nepomukfilewatch.desktop                           powerdevilsuspendsessionaction.desktop
k3bffmpegdecoder.desktop                              nepomukmailfeeder.desktop                          programs.protocol
k3bflacdecoder.desktop                                nepomuknotefeeder.desktop                          proxy.desktop
k3blibsndfiledecoder.desktop                          nepomukontologyloader.desktop                      qimageioplugins
k3bmaddecoder.desktop                                 nepomuk.protocol                                   randr.desktop
k3bmpcdecoder.desktop                                 nepomukqueryservice.desktop                        recentdocuments.desktop
k3boggvorbisdecoder.desktop                           nepomukremovablestorageservice.desktop             remote.protocol
k3boggvorbisencoder.desktop                           nepomuksearch.protocol                             renaudiodlg.desktop
k3bsetup.desktop                                      nepomukstorage.desktop                             renimagedlg.desktop
k3bsoxencoder.desktop                                 nepomukstrigiservice.desktop                       rtsp.protocol
k3bwavedecoder.desktop                                netpref.desktop                                    rtspt.protocol
kaccess.desktop                                       networkinfocategory.desktop                        rtspu.protocol
kactivitymanagerd.desktop                             networkmanagement_novellvpnui.desktop              sambausershareplugin.desktop
kaddressbookpart.desktop                              networkmanagement_openvpnui.desktop                screensaver.desktop
kamera.desktop                                        networkmanagement_pptpui.desktop                   ScreenSavers
katebacktracebrowserplugin.desktop                    networkmanagement_strongswanui.desktop             scsi.desktop
katebuildplugin.desktop                               networkmanagement_vpncui.desktop                   searchproviders
katectagsplugin.desktop                               network.protocol                                   sendfile.desktop
katefilebrowserplugin.desktop                         nfs.protocol                                       ServiceMenus
katefiletemplates.desktop                             nic.desktop                                        settings-accessibility.desktop
katefiletreeplugin.desktop                            nntp.protocol                                      settings-account-details.desktop
kategdbplugin.desktop                                 nntps.protocol                                     settings-application-and-system-notifications.desktop
katekonsoleplugin.desktop                             obexftp.protocol                                   settings-application-appearance-and-behavior.desktop
kate_kttsd.desktop                                    okularComicbook.desktop                            settings-application-appearance.desktop
katemailfilesplugin.desktop                           okularDjvu.desktop                                 settings-audio-and-video.desktop
kateopenheader.desktop                                okularDvi.desktop                                  settings-bluetooth.desktop
katepart.desktop                                      okularEPub.desktop                                 settings-classic-view.desktop
katequickdocumentswitcher.desktop                     okularFax.desktop                                  settings-desktop-appearance.desktop
katesearch.desktop                                    okularFb.desktop                                   settings-display.desktop
katesnippets_tngplugin.desktop                        okularGhostview.desktop                            settings-hardware.desktop
katesql.desktop                                       okularKimgio.desktop                               settings-icon-view.desktop
katesymbolviewer.desktop                              okularOoo.desktop                                  settings-input-devices.desktop
katetabbarextension.desktop                           okular_part.desktop                                settings-locale.desktop
katetabifyplugin.desktop                              okularPlucker.desktop                              settings-lost-and-found.desktop
katetextfilter.desktop                                okularPoppler.desktop                              settings-network-and-connectivity.desktop
katexmlcheck.desktop                                  okularTiff.desktop                                 settings-network-settings.desktop
katexmltools.desktop                                  okularXps.desktop                                  settings-permissions.desktop
kcmaccess.desktop                                     opengl.desktop                                     settings-personal-information.desktop
kcm_akonadi.desktop                                   oseiprovider.desktop                               settings-power-management.desktop
kcm_akonadi_resources.desktop                         phononbackends                                     settings.protocol
kcm_akonadi_server.desktop                            plasma-animator-default.desktop                    settings-removable-devices.desktop
kcmapptsummary.desktop                                plasma-applet-activitybar.desktop                  settings-sharing.desktop
kcm_attica.desktop                                    plasma-applet-analogclock.desktop                  settings-shortcuts-and-gestures.desktop
kcmcgi.desktop                                        plasma-applet-bball.desktop                        settings-startup-and-shutdown.desktop
kcmdolphingeneral.desktop                             plasma-applet-binaryclock.desktop                  settings-system-administration.desktop
kcmdolphinnavigation.desktop                          plasma-applet-blackboard.desktop                   settings-window-behaviour.desktop
kcmdolphinservices.desktop                            plasma-applet-bookmarks.desktop                    settings-workspace-appearance-and-behavior.desktop
kcmdolphinviewmodes.desktop                           plasma-applet-bubblemon.desktop                    settings-workspace-behavior.desktop
kcmgtk.desktop                                        plasma-applet-calculator.desktop                   sftp.protocol
kcm_infosummary.desktop                               plasma-applet-calendar.desktop                     sieve.protocol
kcm_k3bexternalencoder.desktop                        plasma-applet-charselect.desktop                   skype.protocol
kcm_k3boggvorbisencoder.desktop                       plasma-applet-currentappcontrol.desktop            smb.desktop
kcm_k3bsoxencoder.desktop                             plasma-applet-devicenotifier.desktop               smb.protocol
kcmkded.desktop                                       plasma-applet-digitalclock.desktop                 smbstatus.desktop
kcm_kdnssd.desktop                                    plasma-applet-extenderapplet.desktop               smtp.protocol
kcm_keyboard.desktop                                  plasma-applet-eyes.desktop                         smtps.protocol
kcmkmailsummary.desktop                               plasma-applet-fifteenPuzzle.desktop                solid-actions.desktop
kcmkonqyperformance.desktop                           plasma-applet-folderview.desktop                   solidbackends
kcmkontactsummary.desktop                             plasma-applet-icon.desktop                         spellchecking.desktop
kcm_kpimidentities.desktop                            plasma-applet-icontasks.desktop                    standard_actions.desktop
kcmlaunch.desktop                                     plasma-applet-incomingmsg.desktop                  style.desktop
kcmldap.desktop                                       plasma-applet-indicatordisplay.desktop             svgthumbnail.desktop
kcm_mailtransport.desktop                             plasma-applet-katesession.desktop                  system-config-printer-kde.desktop
kcm_memory.desktop                                    plasma-applet-kbstate.desktop                      tar.protocol
kcm_nepomuk.desktop                                   plasma_applet_keyboard.desktop                     tel.protocol
kcm_networkmanagement.desktop                         plasma-applet-kimpanel.desktop                     textthumbnail.desktop
kcm_networkmanagement_tray.desktop                    plasma-applet-knowledgebase.desktop                thumbnail.protocol
kcm_notificationhelper.desktop                        plasma-applet-konqprofiles.desktop                 timeline.protocol
kcmnotify.desktop                                     plasma-applet-konsoleprofiles.desktop              trash.protocol
kcm_partitionmanager.desktop                          plasma-applet-ktorrent.desktop                     useragent.desktop
kcm_pci.desktop                                       plasma-applet-launcher.desktop                     useragentstrings
kcmperformance.desktop                                plasma-applet-leavenote.desktop                    userconfig.desktop
kcm_phonon.desktop                                    plasma-applet-life.desktop                         videodvd.protocol
kcmsdsummary.desktop                                  plasma-applet-lockout.desktop                      wcpotdprovider.desktop
kcmsmserver.desktop                                   plasma-applet-luna.desktop                         webcal.protocol
kcm_solid.desktop                                     plasma-applet-magnifique.desktop                   webdav.protocol
kcm_ssl.desktop                                       plasma-applet-mail_plasmoid.desktop                webdavs.protocol
kcm_synaptiks.desktop                                 plasma-applet-mediaplayer.desktop                  windowsexethumbnail.desktop
kcmtodosummary.desktop                                plasma-applet-menubar.desktop                      windowsimagethumbnail.desktop
kcmtrash.desktop                                      plasma-applet-message-indicator.desktop            workspaceoptions.desktop
kcmusb.desktop                                        plasma-applet-microblog.desktop                    xinerama.desktop
kcm_useraccount.desktop                               plasma-applet-networkmanagement.desktop            xmpp.protocol
kcmview1394.desktop                                   plasma-applet-news.desktop                         xserver.desktop
kconfiguredialog                                      plasma-applet-notifications.desktop                xz.protocol
kded                                                  plasma-applet-nowplaying.desktop                   zeroconf.protocol
kdm.desktop                                           plasma-applet-opendesktop-activities.desktop       zip.protocol
kerfuffle_cli7z.desktop                               plasma-applet-opendesktop.desktop
kerfuffle_clilha.desktop                              plasma-applet-org.kde.showActivityManager.desktop

```

---

### Post by whatthefunk on 2012-06-04
Yes, but there is no .desktop file for any of the shutdown related programs.

---

### Post by ztMAMOHT on 2012-06-04
> **whatthefunk said:**
> Yes, but there is no .desktop file for any of the shutdown related programs.

Yes, I know. So where do I look? :confused:

---

### Post by whatthefunk on 2012-06-04
This is complicated.
This thread tells you haw to tune an icon theme:
[http://www.kubuntuforums.net/showthread.php?26372-HOWTO-create-own-(partial)-icon-theme&p=289332#post289332](http://www.kubuntuforums.net/showthread.php?26372-HOWTO-create-own-(partial)-icon-theme&p=289332#post289332)

What I think you'll have to do is creat a new icon theme from your existing theme in order to make the necessary changes and get all your icons working right.  This process can be aided by the service menu located here:
[http://www.kubuntuforums.net/showthread.php?25740-Service-Menus-with-Dolphin/page4](http://www.kubuntuforums.net/showthread.php?25740-Service-Menus-with-Dolphin/page4)

I havent tried this myself yet, so dont know exactly how it works.  Just trying to point you in the right direction.  If I have time tonight, Ill play around with it to see if I can help you.

---

### Post by ztMAMOHT on 2012-06-06
Solution is found!
In my case theme was installed in "/home/code-priest/.kde/share/icons/Faenza-Dark-Colors/", so I go to "actions" -> "48" and copy/paste one of the icons and rename as "system-reboot.png" then reapply theme and this work.:guitar:

[RIGHT]Many thanks to "whatthefunk" and long life to KDE \\:D/[/RIGHT]

---

