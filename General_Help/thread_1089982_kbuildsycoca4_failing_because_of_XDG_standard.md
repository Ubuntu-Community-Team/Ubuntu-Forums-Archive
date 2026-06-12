---
title: "kbuildsycoca4 failing because of XDG standard"
date: 2009-03-07
forum: General Help
---

### Post by sandyd on 2009-03-07
for some reason, a lot of apps didn't show up in the start menu after the last KDE 4 update.

so i run kbuildsycoca4 in terminal and this weird error shows up
```

kbuildsycoca4(17021) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/euphoria.desktop" is not compliant with XDG standard (missing trailing semicolon). 

```

thats just one of them, theirs a lot of those loooking the same
heres the whole long list if anyone wants to see
```

kbuildsycoca4 running...                                                                                      
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/home/starangyl/.kde-neon/var/tmp/kdecache-starangyl/ksycoca4"                                                           
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::checkVersion: Found version  130 , expecting version  142  or higher.                                                                                                
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/home/starangyl/.kde-neon/var/tmp/kdecache-starangyl/ksycoca4"                                                           
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::checkVersion: Found version  130 , expecting version  142  or higher.                                                                                                
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::checkVersion: Found version  130 , expecting version  142  or higher.                                                                                                
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/home/starangyl/.kde-neon/var/tmp/kdecache-starangyl/ksycoca4"                                                           
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::checkVersion: Found version  130 , expecting version  142  or higher.                                                                                                
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::checkVersion: Found version  130 , expecting version  142  or higher.                                                                                                
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/home/starangyl/.kde-neon/var/tmp/kdecache-starangyl/ksycoca4"                                                           
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::checkVersion: Found version  130 , expecting version  142  or higher.                                                                                                
kbuildsycoca4(18233)/kdecore (KSycoca) KSycocaPrivate::checkVersion: Found version  130 , expecting version  142  or higher.                                                                                                
kbuildsycoca4(18233) KBuildSycoca::recreate: Recreating ksycoca file ("/home/starangyl/.kde-neon/var/tmp/kdecache-starangyl/ksycoca4", version 142)                                                                         
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/audio/x-sbc.xml"                                                                                                      
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-pem-key.xml"                                                                                            
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/vnd.ms-excel.template.macroEnabled.12.xml"                                                                
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/vnd.ms-word.template.macroEnabled.12.xml"                                                                 
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/vnd.openxmlformats-officedocument.presentationml.slideshow.xml"                                           
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/vnd.ms-powerpoint.template.macroEnabled.12.xml"                                                           
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/vnd.ms-excel.sheet.binary.macroEnabled.12.xml"                                                            
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-ssh-key.xml"                                                                                            
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-hcidump.xml"                                                                                            
kbuildsycoca4(18233) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/vnd.ms-powerpoint.slideshow.macroEnabled.12.xml"                                                          
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/starangyl/.config/menus/applications-merged/cxmenu-cxoffice-f769e1da-ae4d-476f-8029-f3873e2c664b.menu"                                          
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/starangyl/.config/menus/applications-merged/cxmenu-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e.menu"                                          
kbuildsycoca4(18233) VFolderMenu::pushDocInfo: Menu "applications-merged/xdg-desktop-menu-dummy.menu" not found.                                                                                                            
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: ""                                       
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/starangyl/.config/menus/applications-merged/cxmenu-cxoffice-0.menu"                                                                             
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/starangyl/.config/menus/applications-merged/cxmenu-cxgames-0.menu"                                                                              
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/applications-merged/kde-multimedia-music.menu"                                                                                         
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/applications-merged/kde-graphics-picasa.menu"                                                                                          
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/applications-merged/system-settings-merge.menu"                                                                                        
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/applications-merged/kde3-multimedia-music.menu"                                                                                        
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/applications-merged/kde-essential.menu"                                                                                                
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/applications-merged/ggz.merge.menu"                                                                                                    
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/ggz.menu"                
kbuildsycoca4(18233) foldNode: "Directory" and "ggz.directory" requires combining!                            
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/kde-settings.menu"       
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/kde-information.menu"    
kbuildsycoca4(18233) foldNode: "Directory" and "kde-information.directory" requires combining!                
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/kde-screensavers.menu"   
kbuildsycoca4(18233) foldNode: "Directory" and "kde-system-screensavers.directory" requires combining!        
kbuildsycoca4(18233) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/etc/xdg/menus/system-settings.menu"    
kbuildsycoca4(18233) VFolderMenu::pushDocInfo: Menu "debian-menu.menu" not found.                             
kbuildsycoca4(18233) VFolderMenu::processLegacyDir: processLegacyDir("/etc/X11/applnk/", "", "")              
kbuildsycoca4(18233) VFolderMenu::processLegacyDir: processLegacyDir("/usr/share/gnome/apps/", "", "")        
kbuildsycoca4(18233) VFolderMenu::processLegacyDir: processLegacyDir("/usr/share/gnome/apps/Internet", "Internet/", "")                                                                                                     
kbuildsycoca4(18233) VFolderMenu::processLegacyDir: processLegacyDir("/usr/share/gnome/apps/Multimedia", "Multimedia/", "")                                                                                                 
kbuildsycoca4(18233) VFolderMenu::processLegacyDir: processLegacyDir("/usr/share/control-center-2.0/capplets/", "", "")                                                                                                     
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/usr/local/share/applications/"                                                                                                          
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/"  
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/kde"                                                                                                             
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/kde/kvpnc.desktop" is not compliant with XDG standard (missing trailing semicolon).                                  
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/kde/kbfx_theme.desktop" is not compliant with XDG standard (missing trailing semicolon).                               
kbuildsycoca4(18233)/kdecore (KService) KServicePrivate::init: The desktop entry file "/usr/share/applications/kde/kdesvn.desktop" has Type= "Application" but also has a X-KDE-Library key. This works for now, but makes user-preference handling difficult, so support for this might be removed at some point. Consider splitting it into two desktop files.                                                                                        
kbuildsycoca4(18233)/kdecore (KService) KServicePrivate::init: The desktop entry file  "/usr/share/applications/kde/koffice.desktop"  has Type= "Application"  but no Exec line                                             

kbuildsycoca4(18233)/kdecore (KService) KBuildServiceFactory::createEntry: Invalid Service :  "/usr/share/applications/kde/koffice.desktop"                                                                                 
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/kde/krita.desktop" is not compliant with XDG standard (missing trailing semicolon).                                    
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/avidemux-qt.desktop" is not compliant with XDG standard (missing trailing semicolon).                                
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/avidemux-qt.desktop" is not compliant with XDG standard (missing trailing semicolon).                                  
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/avidemux-gtk.desktop" is not compliant with XDG standard (missing trailing semicolon).                               
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/avidemux-gtk.desktop" is not compliant with XDG standard (missing trailing semicolon).                                 
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/opera.desktop" is not compliant with XDG standard (missing trailing semicolon).                                      
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/opera.desktop" is not compliant with XDG standard (missing trailing semicolon).                                        
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/kde4"                                                                                                            
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/screensavers"                                                                                                    
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/thunderbird.desktop" is not compliant with XDG standard (missing trailing semicolon).                                  
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/realplay.desktop" is not compliant with XDG standard (missing trailing semicolon).                                   
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/realplay.desktop" is not compliant with XDG standard (missing trailing semicolon).                                     
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gcalctool.desktop" is not compliant with XDG standard (missing trailing semicolon).                                  
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/speedcrunch.desktop" is not compliant with XDG standard (missing trailing semicolon).                                
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/opt/kde-nightly/share/applications/"                                                                                                    
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/opt/kde-nightly/share/applications/kde4"                                                                                                
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.local/share/applications/"                                                                                              
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.wordprocessingml.document.desktop" is not compliant with XDG standard (missing trailing semicolon).            
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/gedit.desktop" is not compliant with XDG standard (missing trailing semicolon).                      
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:video_x-ms-wm.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                      
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.slide::show.desktop" is not compliant with XDG standard (missing trailing semicolon).           
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/gimp.desktop" is not compliant with XDG standard (missing trailing semicolon).                       
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.template.desktop" is not compliant with XDG standard (missing trailing semicolon).              
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:video_x-ms-asf.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                     
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.spreadsheetml.template.desktop" is not compliant with XDG standard (missing trailing semicolon).               
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxgames-0:application_x-crossover-exe::run.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                                       
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.presentation::show.desktop" is not compliant with XDG standard (missing trailing semicolon).    
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.ms-officetheme::show.desktop" is not compliant with XDG standard (missing trailing semicolon).                                               
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:video_x-ms-wmv.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                     
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.presentation.desktop" is not compliant with XDG standard (missing trailing semicolon).          
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0:application_x-crossover-exe::run.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                                      
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.wordprocessingml.template.desktop" is not compliant with XDG standard (missing trailing semicolon).            
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.spreadsheetml.sheet.desktop" is not compliant with XDG standard (missing trailing semicolon).                  
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:video_x-ms-wvx.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                     
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.template::show.desktop" is not compliant with XDG standard (missing trailing semicolon).        
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.ms-officetheme::open.desktop" is not compliant with XDG standard (missing trailing semicolon).                                               
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:audio_x-ms-wax.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                     
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.ms-officetheme.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                     
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.template::open.desktop" is not compliant with XDG standard (missing trailing semicolon).        
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.wordprocessingml.template::open.desktop" is not compliant with XDG standard (missing trailing semicolon).      
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.slide.desktop" is not compliant with XDG standard (missing trailing semicolon).                 
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.slideshow.desktop" is not compliant with XDG standard (missing trailing semicolon).             
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:audio_x-ms-wma.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                     
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:video_avi.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                          
kbuildsycoca4(18233) KConfigGroup::readXdgListEntry: List entry MimeType in "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.spreadsheetml.template::open.desktop" is not compliant with XDG standard (missing trailing semicolon).         
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxgames/desktopdata/cxgames-0/cxmenu/xdg-applications/CrossOver+Games/"                                                 
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/desktopdata/cxoffice-0/cxmenu/xdg-applications/CrossOver/"                                                     
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/"                                               
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Microsoft+Office"                               
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Microsoft+Office/Microsoft+Office+Tools"        
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/ffdshow"                                        
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/ArcSoft+MediaConverter+2.5"                     
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Bibble+Labs"                                    
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Bibble+Labs/Bibble++Pro"                        
"KConfigIni: In file /home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Windows+Media+Player.desktop, line 8: " "Invalid escape sequence "\w"."                                       
"KConfigIni: In file /home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Windows+Media+Player.desktop, line 8: " "Invalid escape sequence "\i"."                                       
"KConfigIni: In file /home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Windows+Media+Player.desktop, line 8: " "Invalid escape sequence "\u"."                                       
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/GTA_3/desktopdata/cxmenu/xdg-applications/Windows+Applications/"                                               
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/GTA_3/desktopdata/cxmenu/xdg-applications/Windows+Applications/Rockstar+Games"                                 
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/GTA_3/desktopdata/cxmenu/xdg-applications/Windows+Applications/Rockstar+Games/GTAIII"                          
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/ffdshow/"                                       
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/ArcSoft+MediaConverter+2.5/"                    
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Bibble+Labs/"                                   
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Bibble+Labs/Bibble++Pro"                        
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Bibble+Labs/Bibble++Pro/"                       
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Microsoft+Office/"                              
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Microsoft+Office/Microsoft+Office+Tools"        
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/winxp/desktopdata/cxmenu/xdg-applications/Windows+Applications/Microsoft+Office/Microsoft+Office+Tools/"       
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/GTA_3/desktopdata/cxmenu/xdg-applications/Windows+Applications/Rockstar+Games/"                                
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/GTA_3/desktopdata/cxmenu/xdg-applications/Windows+Applications/Rockstar+Games/GTAIII"                          
kbuildsycoca4(18233) VFolderMenu::loadApplications: Looking up applications under "/home/starangyl/.cxoffice/GTA_3/desktopdata/cxmenu/xdg-applications/Windows+Applications/Rockstar+Games/GTAIII/"                         
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.              
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "gnome-app-install.desktop"                   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcm_useraccount.desktop"                 
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-desktoppath.desktop"                     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-language.desktop"                        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-spellchecking.desktop"                   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-keyboard_layout.desktop"                 
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcmaccess.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-khotkeys.desktop"                        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-defaultapplication.desktop"              
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-filetypes.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-ksplashthememgr.desktop"                 
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-colors.desktop"                          
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-fonts.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kcmgtk-xdg.desktop"                          
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcmfontinst.desktop"                     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-icons.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-style.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kwindecoration.desktop"                  
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-background.desktop"                      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-screensaver.desktop"                     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-desktopbehavior.desktop"                 
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-desktop.desktop"                         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kwinoptions.desktop"                     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kwinrules.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcmnotify.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-bell.desktop"                            
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-medianotifications.desktop"              
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-clock.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-displayconfig.desktop"                   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-arts.desktop"                            
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-printers.desktop"                        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-userconfig.desktop"                      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-keyboard.desktop"                        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-keys.desktop"                            
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-mouse.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-joystick.desktop"                        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcm_knetworkconfmodule_ss.desktop"       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-proxy.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-netpref.desktop"                         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcm_kdnssd.desktop"                      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcmkrfb.desktop"                         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-fileshare.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-lanbrowser.desktop"                      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcm_btpaired.desktop"                    
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcm_kbluetoothd.desktop"                 
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-mountconfig.desktop"                     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-serviceconfig.desktop"                   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kdm.desktop"                             
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-audioencoding.desktop"                   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kresources.desktop"                      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcmkded.desktop"                         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "kde-kcmsmserver.desktop"                     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Install+Windows+Software.desktop"            
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Configuration.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Documentation.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Terminate+Windows+Applications.desktop"      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Run+a+Windows+Command.desktop"               
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Uninstall.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Install+Windows+Software.desktop"            
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Configuration.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Documentation.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Terminate+Windows+Applications.desktop"      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Run+a+Windows+Command.desktop"               
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Uninstall.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "New+Office+Document.desktop"                 
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Open+Office+Document.desktop"                
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Internet+Explorer.desktop"                   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Windows+Media+Player.desktop"                
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Audio+decoder+configuration.desktop"         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Video+decoder+configuration.desktop"         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "VFW+configuration.desktop"                   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "makeAVIS.desktop"                            
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Uninstall+ffdshow.desktop"                   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Uninstall.desktop"                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Configuration.desktop"                       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "MediaConverter+2.5+for+Philips.desktop"      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Bibble+Pro.desktop"                          
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Remove+Bibble++Pro.desktop"                  
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Read+Me+4.3.desktop"                         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Bibble+Pro+Documentation.desktop"            
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Read+Me.desktop"                             
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Access+2003.desktop"        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Excel+2003.desktop"         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+InfoPath+2003.desktop"      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Outlook+2003.desktop"       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+PowerPoint+2003.desktop"    
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Publisher+2003.desktop"     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Word+2003.desktop"          
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Access+2007.desktop"        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Excel+2007.desktop"         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Groove+2007.desktop"        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+InfoPath+2007.desktop"      
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+OneNote+2007.desktop"       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Outlook+2007.desktop"       
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+PowerPoint+2007.desktop"    
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Publisher+2007.desktop"     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Word+2007.desktop"          
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Digital+Certificate+for+VBA+Projects.desktop"
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Clip+Organizer.desktop"            
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+2003+Language+Settings.desktop"                                                                                                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+2003+Save+My+Settings+Wizard.desktop"                                                                                                     
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Access+Snapshot+Viewer.desktop"                                                                                                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Application+Recovery.desktop"                                                                                                             
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Document+Imaging.desktop"   
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Document+Scanning.desktop"  
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Picture+Manager.desktop"    
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+2007+Language+Settings.desktop"                                                                                                           
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Microsoft+Office+Diagnostics.desktop"        
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Visit+RockstarGames+Website.desktop"         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Uninstall+GTAIII.desktop"                    
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Play+GTAIII.desktop"                         
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "Read+Me.desktop"                             
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "emacs.desktop"                               
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "picasa.desktop"                              
kbuildsycoca4(18233) VFolderMenu::processCondition: Adding file "picasa-fontcfg.desktop"                      
kbuildsycoca4(18233) VFolderMenu::processMenu: Moving "Settings/Information" to "Information"                 
kbuildsycoca4(18233) VFolderMenu::processKDELegacyDirs:                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.slideshow.desktop" specifies undefined mimetype/servicetype "application/x-crossover-ppsx"                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-7z-compressed-tar"                                   
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ar"                                                  
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1"                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1-compressed-tar"                                
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-cabinet"                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ear"                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-lzop-compressed-tar"                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rar-compressed"                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rzip"                                                
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-war"                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-zip"                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "multipart/x-zip"                                                   
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/brasero-open-image.desktop" specifies undefined mimetype/servicetype "application/x-toc"                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/nautilus-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/nautilus-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/normal"                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "application/x-annodex"                                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-quicktime"                                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mkv"                                                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/msvideo"                                                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"                                                                   
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"                                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-basic"                                                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"                                                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-8svx"                                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/8svx"                                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-16sv"                                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/168sv"                                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/ilbm"                                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/anim"                                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/x-png"                                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mng"                                                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"                                                                
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"                                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"                                                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"                                                            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg2"                                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg2"                                                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"                                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg3"                                                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "x-mpegurl"                                                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/dragonplayer_play_dvd.desktop" specifies undefined mimetype/servicetype "media/dvdvideo"                                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/jpg"                                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-gray"                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-png"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-ciff"                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-mrw"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-x3f"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-orf"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-nef"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-cr2"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/f-spot-view.desktop" specifies undefined mimetype/servicetype "image/x-raf"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/amarok-nightly.desktop" specifies undefined mimetype/servicetype "audio/vorbis"                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/amarok-nightly.desktop" specifies undefined mimetype/servicetype "audio/x-oggflac"                              
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/amarok-nightly.desktop" specifies undefined mimetype/servicetype "audio/x-vorbis"                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.template::show.desktop" specifies undefined mimetype/servicetype "application/x-crossover-potx"            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.template::open.desktop" specifies undefined mimetype/servicetype "application/x-crossover-potx"            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/pcx"                                              
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/x-icon"                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/x-xcf-gimp"                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde/kbfx_theme.desktop" specifies undefined mimetype/servicetype "application/x-kbfxtheme"                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/gfloppy.desktop" specifies undefined mimetype/servicetype "x-device/floppy"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:video_x-ms-asf.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-asf"                                                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/qt3config.desktop" specifies undefined mimetype/servicetype "application/x-qtconfig"                                              
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.wordprocessingml.template::open.desktop" specifies undefined mimetype/servicetype "application/x-crossover-dotx"          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.presentation.desktop" specifies undefined mimetype/servicetype "application/x-crossover-pptx"              
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde/kdenlive.desktop" specifies undefined mimetype/servicetype "application/vnd.kde.kdenlive"                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.wordprocessingml.template.desktop" specifies undefined mimetype/servicetype "application/x-crossover-dotx"                
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/openoffice.org3-writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "application/x-smil"                                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "application/streamingmedia"                                            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "application/x-streamingmedia"                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "application/vnd.rn-realmedia-vbr"                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/x-aac"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/m4a"                                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/mp1"                                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/x-mp1"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/x-mp2"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/mpg"                                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/x-mpg"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/rn-mpeg"                                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/scpls"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-pcm"                                                
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"                                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "audio/x-pls"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "video/x-mpeg2"                                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "video/msvideo"                                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "video/x-ms-afs"                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "video/x-ms-wvxvideo"                                                   
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/mplayer.desktop" specifies undefined mimetype/servicetype "video/x-theora"                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.spreadsheetml.template.desktop" specifies undefined mimetype/servicetype "application/x-crossover-xltx"                   
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/evince.desktop" specifies undefined mimetype/servicetype "application/x-cb7"                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/evince.desktop" specifies undefined mimetype/servicetype "image/*"                                                                
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.spreadsheetml.template::open.desktop" specifies undefined mimetype/servicetype "application/x-crossover-xltx"             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/jpg"                                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-gray"                                                              
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-png"                                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:audio_x-ms-wax.desktop" specifies undefined mimetype/servicetype "application/x-crossover-wax"                                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:video_x-ms-wvx.desktop" specifies undefined mimetype/servicetype "application/x-crossover-wvx"                                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/mpg"                                                            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-mpg"                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-pcm"                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/vnd.rn-realmedia-secure"                                  
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/vnd.rn-realaudio-secure"                                  
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio-secure"                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "video/vnd.rn-realvideo-secure"                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"                                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/vnd.rn-realmedia-vbr"                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/vnd.rn-realsystem-rmj"                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/vnd.rn-realsystem-rmx"                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-aac"                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/m4a"                                                            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/rn-mpeg"                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/scpls"                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/x-smil"                                                   
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/smil+xml"                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/streamingmedia"                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/x-streamingmedia"                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "video/mpeg4-generic"                                                  
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/vnd.rn-wma"                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/realplay.desktop" specifies undefined mimetype/servicetype "application/vnd.rn-wmv"                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/easytag.desktop" specifies undefined mimetype/servicetype "x-directory/normal"                                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/avidemux-gtk.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"                                                     
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.template.desktop" specifies undefined mimetype/servicetype "application/x-crossover-potx"                  
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.presentationml.presentation::show.desktop" specifies undefined mimetype/servicetype "application/x-crossover-pptx"        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/onboard-settings.desktop" specifies undefined mimetype/servicetype "application/x-onboardsettings"                                
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/avidemux-qt.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/comix.desktop" specifies undefined mimetype/servicetype "image/x-icon"                                                            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/comix.desktop" specifies undefined mimetype/servicetype "application/x-zip"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/comix.desktop" specifies undefined mimetype/servicetype "image/svg"                                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/comix.desktop" specifies undefined mimetype/servicetype "image/svg-xml"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/comix.desktop" specifies undefined mimetype/servicetype "image/vnd.adobe.svg+xml"                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/comix.desktop" specifies undefined mimetype/servicetype "text/xml-svg"                                                            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/opera.desktop" specifies undefined mimetype/servicetype "image/x-xbm"                                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/opera.desktop" specifies undefined mimetype/servicetype "application/mime"                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"                                                              
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/msvideo"                                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-flc"                                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"                                                            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-flac"                                                        
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "misc/ultravox"                                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"                                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"                                                            
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"                                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/audiocd_play.desktop" specifies undefined mimetype/servicetype "media/audiocd"                                                               
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/onboard.desktop" specifies undefined mimetype/servicetype "application/x-onboard"                                                 
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/smil+xml"                                                    
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"                                             
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/x-flac"                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "application/x-smil"                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"                                                         
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"                                                  
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"                                                       
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"                                                      
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "audio/x-vorbis"                                                          
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "misc/ultravox"                                                           
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/totem.desktop" specifies undefined mimetype/servicetype "video/x-totem-stream"
kbuildsycoca4(18233) KBuildServiceFactory::populateServiceTypes: "/home/starangyl/.local/share/applications/cxassoc-cxoffice-0a69c7eb-505e-455f-a57c-12c9c77eb29e:application_vnd.openxmlformats-officedocument.spreadsheetml.sheet.desktop" specifies undefined mimetype/servicetype "application/x-crossover-xlsx"
kbuildsycoca4(18233) KMimeAssociations::parseAllMimeAppsList: Parsing "/home/starangyl/.local/share/applications/mimeapps.list"
kbuildsycoca4(18233) KMimeAssociations::parseAddedAssociations: "/home/starangyl/.local/share/applications/mimeapps.list" specifies unknown service "kde-kfmclient_dir.desktop" in "Added Associations"
kbuildsycoca4(18233) KMimeFileParser::parseGlobFiles: Now parsing "/usr/local/share/mime/globs2"
kbuildsycoca4(18233) KMimeFileParser::parseGlobFiles: Now parsing "/usr/share/mime/globs2"
kbuildsycoca4(18233) KMimeFileParser::parseGlobFiles: Now parsing "/home/starangyl/.local/share/mime/globs2"


```

any ideassss?

---

