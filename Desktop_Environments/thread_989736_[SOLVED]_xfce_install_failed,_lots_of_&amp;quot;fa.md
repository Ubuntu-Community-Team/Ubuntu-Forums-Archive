---
title: "[SOLVED] xfce install failed, lots of &amp;quot;failed&amp;quot; downloads"
date: 2008-11-21
forum: Desktop Environments
---

### Post by slinkey1981 on 2008-11-21
So I tried installing the "xubuntu-desktop" and all of it's lovely dependencies over Ubuntu 8.04, and man, did I get a lot of server failures. I tried it a second time, and it's still a no-go.

Anyone know of any other way I can get this to work?

I did not let Synaptic go ahead with the installation, as I would like my computer to work. And I have no idea how many of the failed items are essential for xfce.

Here's my Synaptic error log.
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-gnome-1-114_1.14.7-2ubuntu1_i386.deb
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31), connection timed out


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/goffice/libgoffice-0-6_0.6.1-1ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnumeric/gnumeric-gtk_1.8.2-1ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-icon-theme/xfce4-icon-theme_4.4.2-1_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gtk2-engines-xfce/gtk2-engines-xfce_2.4.2-1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libx/libxfce4util/libxfce4util4_4.4.2-2ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libx/libxfce4mcs/libxfce4mcs-client3_4.4.2-3_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libx/libxfce4mcs/libxfce4mcs-manager3_4.4.2-3_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libx/libxfcegui4/libxfcegui4-4_4.4.2-1ubuntu2_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/e/exo/libexo-0.3-0_0.3.4-3ubuntu4_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/glib2.0/libglib2.0-data_2.16.6-0ubuntu1_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtagc0_1.4-8ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar/thunar-data_0.9.0-4ubuntu2_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar/libthunar-vfs-1-2_0.9.0-4ubuntu2_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mousepad/mousepad_0.2.13-2ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce-mcs-manager/xfce4-mcs-manager_4.4.2-2ubuntu2_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel/xfce4-panel_4.4.2-3ubuntu3_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/orage/orage_4.5.12.2-5ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin-otr/pidgin-otr_3.1.0-1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/e/exo/python-exo_0.3.4-3ubuntu4_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim-tables/scim-modules-table_0.5.7-2ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim-tables/scim-tables-additional_0.5.7-2ubuntu1_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tango-icon-theme/tango-icon-theme_0.8.1-3_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tango-icon-theme-common/tango-icon-theme-common_0.7-0ubuntu1_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar/thunar_0.9.0-4ubuntu2_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar-archive-plugin/thunar-archive-plugin_0.2.4-3ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar-media-tags-plugin/thunar-media-tags-plugin_0.1.2-1ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar-thumbnailers/thunar-thumbnailers_0.3.0-1ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/thunar-volman/thunar-volman_0.2.0-2ubuntu2_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.1-138+1ubuntu3_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-appfinder/xfce4-appfinder_4.4.2-1ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-battery-plugin/xfce4-battery-plugin_0.5.0-6ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-clipman-plugin/xfce4-clipman-plugin_0.8.1-1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-cpugraph-plugin/xfce4-cpugraph-plugin_0.4.0-0ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-dict-plugin/xfce4-dict-plugin_0.2.1-1ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-fsguard-plugin/xfce4-fsguard-plugin_0.4.1-1ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-governor-plugin/xfce4-governor-plugin_0.1.0-0ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-mailwatch-plugin/xfce4-mailwatch-plugin_1.0.1-2ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce-mcs-plugins/xfce4-mcs-plugins_4.4.2-3ubuntu5_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-mixer/xfce4-mixer-alsa_4.4.2-2ubuntu2_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-mixer/xfce4-mixer_4.4.2-2ubuntu2_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-mount-plugin/xfce4-mount-plugin_0.5.4-0ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-netload-plugin/xfce4-netload-plugin_0.4.0-3ubuntu2.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-notes-plugin/xfce4-notes-plugin_1.6.1-1ubuntu2_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-quicklauncher-plugin/xfce4-quicklauncher-plugin_1.9.4-1ubuntu3_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-screenshooter-plugin/xfce4-screenshooter-plugin_1.0.0-3ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-session/xfce4-session_4.4.2-2ubuntu2.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-smartbookmark-plugin/xfce4-smartbookmark-plugin_0.4.2-1ubuntu2.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-systemload-plugin/xfce4-systemload-plugin_0.4.2-1ubuntu3_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-terminal/xfce4-terminal_0.2.8-4ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-utils/xfce4-utils_4.4.2-4ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-verve-plugin/xfce4-verve-plugin_0.3.5-1ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-weather-plugin/xfce4-weather-plugin_0.6.2-1ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-xkb-plugin/xfce4-xkb-plugin_0.4.3-1ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfdesktop4/xfdesktop4-data_4.4.2-5ubuntu1.1_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfdesktop4/xfdesktop4_4.4.2-5ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfprint4/xfprint4_4.4.2-1ubuntu3_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfwm4/xfwm4_4.4.2-2ubuntu1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfwm4-themes/xfwm4-themes_4.4.2-1_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xubuntu-artwork/xubuntu-artwork-usplash_0.19_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xubuntu-default-settings/xubuntu-default-settings_0.39.1_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce-mcs-plugins-extra/xfce4-mcs-plugins-extra_1.0.1-0ubuntu3_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xubuntu-meta/xubuntu-desktop_2.66_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xubuntu-docs/xubuntu-docs_8.04.2.1_all.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/r/ristretto/ristretto_0.0.18-1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-places-plugin/xfce4-places-plugin_1.0.0-1ubuntu1.1_i386.deb
  Unable to connect to us.archive.ubuntu.com http:
```

After 3rd try, I have the following "Failed" downloads.

libgsf-gnome-1-114 
xfce4-icon-theme

---

### Post by taurus on 2008-11-21
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and use the Main Server.  Then, press reload and close down synaptic.

What happens when you run these two commands from a terminal now?

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by frankleeee on 2008-11-21
I have downloaded xubuntu-desktop into 3 computers from the main server in the last week with no problems.

---

### Post by EV500B on 2008-11-22
You can try to change the mirror server.

---

### Post by slinkey1981 on 2008-11-22
> **taurus said:**
> Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and use the Main Server.  Then, press reload and close down synaptic.

What happens when you run these two commands from a terminal now?

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

Using the main server helped. Thank You!

---

