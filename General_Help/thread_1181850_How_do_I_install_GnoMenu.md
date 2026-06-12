---
title: "How do I install GnoMenu"
date: 2009-06-08
forum: General Help
---

### Post by Arkaman on 2009-06-08
How do I install this? 

[http://www.gtk-apps.org/content/show.php/GnoMenu+-+consolidated+menu+for](http://www.gtk-apps.org/content/show.php/GnoMenu+-+consolidated+menu+for)
+gnome?content=93056

They say to put make install in terminal but that does not work.

---

### Post by s.fox on 2009-06-08
Hi,

Are your file paths correct?  Can you please also post your error message you received in the terminal.

Thanks.

-Ash R

---

### Post by michy99 on 2009-06-08
Usually, you must run make install with sudo  for root permissions.```
sudo make install
```

---

### Post by Arkaman on 2009-06-08
When I run sudo make install it gives me this error


vaughn@vaughn-desktop:~$ sudo make install
[sudo] password for vaughn: 
make: *** No rule to make target `install'.  Stop.
vaughn@vaughn-desktop:~$

---

### Post by michy99 on 2009-06-08
Are you running it from the extracted directory? I assume you have extracted the tar.gz file. If so there is usually a readme file that should tell you how to install.

---

### Post by Arkaman on 2009-06-08
Yes I extracted it.  All the readme said was put in sudo make install.  I just went to app>terminal  IDK if thats the wrong thing to do.

---

### Post by Arkaman on 2009-06-08
vaughn@vaughn-desktop:~$ cd /home/vaughn/Desktop/gnomenu
vaughn@vaughn-desktop:~/Desktop/gnomenu$ cd /home/vaughn/Desktop
vaughn@vaughn-desktop:~/Desktop$ tar xvfz gnomenu-1.9.9.tar.gz
gnomenu/
gnomenu/src/
gnomenu/src/share/
gnomenu/src/lib/
gnomenu/src/bin/
gnomenu/src/share/gnomenu/
gnomenu/src/lib/gnomenu/
gnomenu/src/lib/bonobo/
gnomenu/src/share/gnomenu/Themes/
gnomenu/src/lib/gnomenu/locale/
gnomenu/src/lib/gnomenu/graphics/
gnomenu/src/lib/gnomenu/backup/
gnomenu/src/share/gnomenu/Themes/Menu/
gnomenu/src/share/gnomenu/Themes/Icon/
gnomenu/src/share/gnomenu/Themes/Button/
gnomenu/src/share/gnomenu/Themes/Menu/Avio/
gnomenu/src/share/gnomenu/Themes/Menu/Short/
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/
gnomenu/src/share/gnomenu/Themes/Menu/Blue/
gnomenu/src/share/gnomenu/Themes/Menu/Glow/
gnomenu/src/share/gnomenu/Themes/Menu/Kore/
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/
gnomenu/src/share/gnomenu/Themes/Menu/Vista/
gnomenu/src/share/gnomenu/Themes/Menu/XP/
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/
gnomenu/src/share/gnomenu/Themes/Menu/Glass/
gnomenu/src/share/gnomenu/Themes/Menu/Slab/
gnomenu/src/share/gnomenu/Themes/Menu/Kde/
gnomenu/src/share/gnomenu/Themes/Icon/BW/
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/
gnomenu/src/share/gnomenu/Themes/Icon/Vista/
gnomenu/src/share/gnomenu/Themes/Button/GnomeButton/
gnomenu/src/share/gnomenu/Themes/Button/Black-White 2/
gnomenu/src/share/gnomenu/Themes/Button/Arch/
gnomenu/src/share/gnomenu/Themes/Button/Glow/
gnomenu/src/share/gnomenu/Themes/Button/GnoBlue/
gnomenu/src/share/gnomenu/Themes/Button/Gnome/
gnomenu/src/share/gnomenu/Themes/Button/Iniciar/
gnomenu/src/share/gnomenu/Themes/Button/Ubuntu/
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/
gnomenu/src/share/gnomenu/Themes/Button/XP/
gnomenu/README.txt
gnomenu/Makefile
gnomenu/Changelog
gnomenu/COPYING
gnomenu/MANIFEST.in
gnomenu/src/bin/GnoMenu.py
gnomenu/src/bin/GnoMenu.py~
gnomenu/src/lib/gnomenu/globalkeybinding.py
gnomenu/src/lib/gnomenu/GnoMenu-Settings.py
gnomenu/src/lib/gnomenu/Menu_Main.py
gnomenu/src/lib/gnomenu/Menu_Widgets.py
gnomenu/src/lib/gnomenu/Panel_Top.py
gnomenu/src/lib/gnomenu/geany_run_script.sh
gnomenu/src/lib/gnomenu/Start_Script.sh
gnomenu/src/lib/gnomenu/translators.txt
gnomenu/src/lib/gnomenu/menuiconcachetemplate.xml
gnomenu/src/lib/gnomenu/Gnome_run_dialog.py
gnomenu/src/lib/gnomenu/Gnome_menu.py
gnomenu/src/lib/gnomenu/DesktopIntegration.py
gnomenu/src/lib/gnomenu/GnoMenu.py
gnomenu/src/lib/gnomenu/Globals.py
gnomenu/src/lib/gnomenu/Panel_Object.py
gnomenu/src/lib/gnomenu/Popup_Menu.py
gnomenu/src/lib/gnomenu/Menu_Items.py
gnomenu/src/lib/bonobo/GNOME_GnoMenu.server
gnomenu/src/lib/gnomenu/locale/Settings_LangPack_cs.xml
gnomenu/src/lib/gnomenu/locale/Settings_LangPack_en.xml
gnomenu/src/lib/gnomenu/locale/Settings_LangPack_en_US.xml
gnomenu/src/lib/gnomenu/locale/Settings_LangPack_es.xml
gnomenu/src/lib/gnomenu/locale/Settings_LangPack_fr.xml
gnomenu/src/lib/gnomenu/locale/Settings_LangPack_pt.xml
gnomenu/src/lib/gnomenu/locale/Settings_LangPack_pt_BR.xml
gnomenu/src/lib/gnomenu/locale/Settings_LangPack_pt_PT.xml
gnomenu/src/lib/gnomenu/graphics/language.png
gnomenu/src/lib/gnomenu/graphics/logo.png
gnomenu/src/lib/gnomenu/graphics/selected.png
gnomenu/src/lib/gnomenu/graphics/theme.png
gnomenu/src/lib/gnomenu/graphics/unselected.png
gnomenu/src/lib/gnomenu/graphics/brokenlink.png
gnomenu/src/lib/gnomenu/backup/GnoMenu-Settings.py
gnomenu/src/lib/gnomenu/backup/settings-window.gladep
gnomenu/src/lib/gnomenu/backup/settings-window.glade
gnomenu/src/lib/gnomenu/backup/Settings_default.xml
gnomenu/src/lib/gnomenu/backup/Processes.py
gnomenu/src/lib/gnomenu/backup/error-message.glade
gnomenu/src/lib/gnomenu/backup/error_message.py
gnomenu/src/lib/gnomenu/backup/GNOME_VistaMenu.server
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_pictures.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_music.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_games.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_none.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_connect.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_power.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_recentitems.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_synaptic.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_computer.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_controlpanel.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_documents.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_help.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_search.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_home.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_lock.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/m_network.png
gnomenu/src/share/gnomenu/Themes/Menu/Avio/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/m_searchbar_light.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/m_all_apps_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/Custom_Settings.py
gnomenu/src/share/gnomenu/Themes/Menu/Short/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/m_aux_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/.png
gnomenu/src/share/gnomenu/Themes/Menu/Short/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Short/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/Custom_Settings.py
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_aux.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_aux_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_lock.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_power.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_searchbar_dark.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/m_submenu_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/BlackVista/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_computer.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_connect.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_controlpanel.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_documents.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_help.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_lock_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_lock_icon_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_music.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_network.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_pictures.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_power_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_power_icon_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_recentitems.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_run.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_search.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_synaptic.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/m_all_apps.png
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/BlackXP/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/Blue/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Blue/Custom_Settings.py
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_aux.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_aux_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_lock.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_power.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_searchbar_light.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/m_submenu_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/Blue/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_aux.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_aux_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_lock.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_power.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/m_submenu_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Glow/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Glow/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/m_aux_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/m_searchbar.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/Kore/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Kore/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_computer.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_connect.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_controlpanel.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_documents.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_help.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_lock_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_lock_icon_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_music.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_network.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_pictures.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_power_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_power_icon_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_recentitems.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_run.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_search.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_synaptic.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/SilverXP/m_all_apps.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/Vista/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Vista/SearchBar.py~
gnomenu/src/share/gnomenu/Themes/Menu/Vista/Custom_Settings.py
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_aux.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_aux_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_lock.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_power.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_searchbar_light.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/m_submenu_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Vista/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_computer.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_connect.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_controlpanel.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_documents.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_help.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_lock_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_lock_icon_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_music.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_network.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_pictures.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_power_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_power_icon_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_recentitems.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_run.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_search.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_synaptic.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/m_all_apps.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/XP/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/XP/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/start-menu.xcf
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/m_searchbar.png
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/SlicknesS/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/Glass/Custom_Settings.py
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_aux.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_aux_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_button.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_lock.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_lock_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_power.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_power_sel.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_searchbar_light.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_separator.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/m_submenu_icon.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/Glass/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/Glass/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Slab/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/Slab/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Slab/shutdown.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/pmanager.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/lock.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/isoftware.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/help.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/search.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/logout.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/cpanel.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/but2.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/tab.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/searchbar.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/but.png
gnomenu/src/share/gnomenu/Themes/Menu/Slab/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/themedata.xml
gnomenu/src/share/gnomenu/Themes/Menu/Kde/start-menu (cópia).png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/m_apps.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/m_shutdown.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/m_computer.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/m_recent.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/m_tab.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/start-menu.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/user-image-frame.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/themepreview.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/m_favorite.png
gnomenu/src/share/gnomenu/Themes/Menu/Kde/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Menu/Kde/Custom_Settings.py
gnomenu/src/share/gnomenu/Themes/Icon/BW/.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/firefox_icon.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_computer.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_connect.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_controlpanel.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_defaults.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_documents.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_games.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_help.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_home.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_music.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_network.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_pictures.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_recentitems.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_search.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_synaptic.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/m_videos.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/no-user-image.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/themedata.xml
gnomenu/src/share/gnomenu/Themes/Icon/BW/themepreview.png
gnomenu/src/share/gnomenu/Themes/Icon/BW/thunderbird_icon.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/firefox_icon.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_computer.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_connect.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_controlpanel.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_documents.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_games.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_help.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_home.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_music.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_network.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_pictures.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_recentitems.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_search.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_synaptic.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/m_videos.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/no-user-image.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/themedata.xml
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/themepreview.png
gnomenu/src/share/gnomenu/Themes/Icon/Newstyles/thunderbird_icon.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_computer.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/firefox_icon.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_connect.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_controlpanel.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_documents.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_games.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_help.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_home.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_music.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_network.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_pictures.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_recentitems.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_search.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_synaptic.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/m_videos.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/no-user-image.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Icon/Vista/themepreview.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/thunderbird_icon.png
gnomenu/src/share/gnomenu/Themes/Icon/Vista/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/GnomeButton/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/GnomeButton/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/GnomeButton/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/GnomeButton/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/GnomeButton/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/Black-White 2/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Black-White 2/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/Black-White 2/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Black-White 2/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/Black-White 2/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/Black-White 2/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here-bottom-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here-bottom-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here-bottom.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here-top-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here-top-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here-top.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/Arch/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/Arch/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/Glow/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Glow/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Glow/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/Glow/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/Glow/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/Glow/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/GnoBlue/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/GnoBlue/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/GnoBlue/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/GnoBlue/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/GnoBlue/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/GnoBlue/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/Gnome/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Gnome/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Gnome/start-here-top-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Gnome/start-here-top-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Gnome/start-here-top.png
gnomenu/src/share/gnomenu/Themes/Button/Gnome/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/Gnome/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/Gnome/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/Gnome/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/Iniciar/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Iniciar/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Iniciar/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/Iniciar/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/Iniciar/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/Iniciar/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/Ubuntu/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/Ubuntu/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/Ubuntu/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/Ubuntu/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/Ubuntu/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/Ubuntu/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/start-here-top-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/start-here-top-glow.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/start-here-top.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuLogo/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/start-here-top-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/start-here-top-glow.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/start-here-top.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/UbuntuOrb/themepreview.png
gnomenu/src/share/gnomenu/Themes/Button/XP/themedata.xml
gnomenu/src/share/gnomenu/Themes/Button/XP/themedata.xml~
gnomenu/src/share/gnomenu/Themes/Button/XP/start-here-depressed.png
gnomenu/src/share/gnomenu/Themes/Button/XP/start-here.png
gnomenu/src/share/gnomenu/Themes/Button/XP/start-here-glow.png
gnomenu/src/share/gnomenu/Themes/Button/XP/themepreview.png
vaughn@vaughn-desktop:~/Desktop$ cd gnomenu
vaughn@vaughn-desktop:~/Desktop/gnomenu$ ./congigure
bash: ./congigure: No such file or directory
vaughn@vaughn-desktop:~/Desktop/gnomenu$ make
Makefile: Available actions: install, uninstall,
vaughn@vaughn-desktop:~/Desktop/gnomenu$ su -c make install password
Unknown id: install
vaughn@vaughn-desktop:~/Desktop/gnomenu$ su -c "make install" password
Unknown id: firewood
vaughn@vaughn-desktop:~/Desktop/gnomenu$ su -c "make install" (password)
bash: syntax error near unexpected token `('
vaughn@vaughn-desktop:~/Desktop/gnomenu$ su -c "make install"
password: 
su: Authentication failure
vaughn@vaughn-desktop:~/Desktop/gnomenu$

---

### Post by michy99 on 2009-06-08
I noticed that you mis-spelled configure in the ./configure command. Might try again. You were in the gnomenu directory this time so that part is right. The usual chain of events is```
./configure
make
sudo make install
```but in this case you may only need```
sudo make install
```If neither one works, post the readme file here.

---

### Post by Arkaman on 2009-06-08
WOOT Thanks I got it now. THANKS!!!!

---

### Post by proverbs308 on 2009-07-23
I did all that but how do I access the program to run it?

---

