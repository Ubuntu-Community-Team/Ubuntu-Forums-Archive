---
title: "Compositor on GNOME vanilla vs Ubuntu-Desktop"
date: 2024-07-02
forum: Desktop Environments
---

### Post by GogoM on 2024-07-02
On a HP Eliteboot 840 I installed Ubuntu Server image. Then I installed Gnome Vanilla package. I didn't notice any compositor glitches until UEFA Euro Cup started so now I'm using Acestream to watch it. 
When using GNOME there's a breakage in the screen, couple of lines, about an inch, where the picture lags a bit in between those lines. Just like when there's no compositor.
Then I installed ubuntu-desktop and when logged in to Ubuntu the picture doesn't break, but when logged in to GNOME GUI the picture still breaks. 
Wayland doesn't seem to have been installed, X11 is running.

Why is Ubuntu Desktop better when it comes to watching video stream vs GNOME?

I thought it could have been a package that got installed along with ubuntu-desktop packages, something to do with compositor, but wouldn't GNOME have access to that package then as well?

Here's a list of packages that got installed when I installed ubuntu-desktop. I don't see anything relevant to picture composition quality.

Log is from today and yesterday, because I installed it and removed it then put it back because the picture is much better when using Ubuntu desktop.

```

&#10140;  ~ grep " install " /var/log/dpkg.log                    
2024-07-01 22:07:35 install thunderbird:amd64 <none> 2:1snap1-0ubuntu3
2024-07-01 22:08:10 install apt-config-icons-hidpi:all <none> 1.0.2-1build6
2024-07-01 22:08:10 install dmz-cursor-theme:all <none> 0.4.5ubuntu1
2024-07-01 22:08:10 install fonts-noto-core:all <none> 20201225-2
2024-07-01 22:08:11 install gamemode-daemon:amd64 <none> 1.8.1-2build1
2024-07-01 22:08:11 install libgamemode0:amd64 <none> 1.8.1-2build1
2024-07-01 22:08:11 install libgamemodeauto0:amd64 <none> 1.8.1-2build1
2024-07-01 22:08:11 install gamemode:amd64 <none> 1.8.1-2build1
2024-07-01 22:08:11 install gir1.2-gnomeautoar-0.1:amd64 <none> 0.4.4-2build4
2024-07-01 22:08:11 install gir1.2-gnomedesktop-3.0:amd64 <none> 44.0-5build2
2024-07-01 22:08:12 install gnome-clocks:amd64 <none> 46.0-1build1
2024-07-01 22:08:12 install gnome-power-manager:amd64 <none> 43.0-2build2
2024-07-01 22:08:12 install gnome-shell-extension-appindicator:all <none> 58-1
2024-07-01 22:08:12 install gnome-shell-extension-desktop-icons-ng:all <none> 46+really47.0.9-1
2024-07-01 22:08:13 install gnome-shell-extension-ubuntu-dock:all <none> 90ubuntu1
2024-07-01 22:08:13 install gnome-shell-extension-ubuntu-tiling-assistant:all <none> 46-1ubuntu1
2024-07-01 22:08:13 install liblttng-ust-common1t64:amd64 <none> 2.13.7-1.1ubuntu2
2024-07-01 22:08:13 install liblttng-ust-ctl5t64:amd64 <none> 2.13.7-1.1ubuntu2
2024-07-01 22:08:13 install liblttng-ust1t64:amd64 <none> 2.13.7-1.1ubuntu2
2024-07-01 22:08:13 install libcamera0.2:amd64 <none> 0.ver2.0.r0.g89227a42-8~ubuntu24.04
2024-07-01 22:08:14 install gstreamer1.0-libcamera:amd64 <none> 0.ver2.0.r0.g89227a42-8~ubuntu24.04
2024-07-01 22:08:14 install gnome-snapshot:amd64 <none> 46.2-1ubuntu2
2024-07-01 22:08:14 install gsettings-ubuntu-schemas:all <none> 0.0.7+21.10.20210712-0ubuntu3
2024-07-01 22:08:14 install gstreamer1.0-packagekit:amd64 <none> 1.2.8-2build3
2024-07-01 22:08:14 install gtk2-engines-murrine:amd64 <none> 0.98.2-4
2024-07-01 22:08:14 install ldap-utils:amd64 <none> 2.6.7+dfsg-1~exp1ubuntu8
2024-07-01 22:08:14 install libavahi-ui-gtk3-0:amd64 <none> 0.8-13ubuntu6
2024-07-01 22:08:14 install libbasicobjects0t64:amd64 <none> 0.6.2-2.1build1
2024-07-01 22:08:14 install libcollection4t64:amd64 <none> 0.6.2-2.1build1
2024-07-01 22:08:14 install libdhash1t64:amd64 <none> 0.6.2-2.1build1
2024-07-01 22:08:14 install libfprint-2-tod1:amd64 <none> 1:1.94.7+tod1-0ubuntu5~24.04.1
2024-07-01 22:08:14 install libfprint-2-2:amd64 <none> 1:1.94.7+tod1-0ubuntu5~24.04.1
2024-07-01 22:08:15 install libgamemode0:i386 <none> 1.8.1-2build1
2024-07-01 22:08:15 install libgamemodeauto0:i386 <none> 1.8.1-2build1
2024-07-01 22:08:15 install libpath-utils1t64:amd64 <none> 0.6.2-2.1build1
2024-07-01 22:08:15 install libref-array1t64:amd64 <none> 0.6.2-2.1build1
2024-07-01 22:08:15 install libini-config5t64:amd64 <none> 0.6.2-2.1build1
2024-07-01 22:08:15 install libipa-hbac0t64:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:15 install libpam-pwquality:amd64 <none> 1.4.5-3build1
2024-07-01 22:08:15 install libsasl2-modules-gssapi-mit:amd64 <none> 2.1.28+dfsg1-5ubuntu3
2024-07-01 22:08:15 install nautilus-sendto:amd64 <none> 3.8.6-7build2
2024-07-01 22:08:15 install remmina-common:all <none> 1.4.35+dfsg-0ubuntu5
2024-07-01 22:08:15 install remmina:amd64 <none> 1.4.35+dfsg-0ubuntu5
2024-07-01 22:08:15 install remmina-plugin-rdp:amd64 <none> 1.4.35+dfsg-0ubuntu5
2024-07-01 22:08:16 install remmina-plugin-secret:amd64 <none> 1.4.35+dfsg-0ubuntu5
2024-07-01 22:08:16 install remmina-plugin-vnc:amd64 <none> 1.4.35+dfsg-0ubuntu5
2024-07-01 22:08:16 install shotwell-common:all <none> 0.32.6-1ubuntu1
2024-07-01 22:08:16 install systemd-oomd:amd64 <none> 255.4-1ubuntu8.1
2024-07-01 22:08:16 install ubuntu-desktop-minimal:amd64 <none> 1.539
2024-07-01 22:08:16 install ubuntu-desktop:amd64 <none> 1.539
2024-07-01 22:08:16 install ubuntu-report:amd64 <none> 1.7.3build2
2024-07-01 22:08:16 install xcursor-themes:all <none> 1.0.6-0ubuntu1
2024-07-01 22:08:16 install yaru-theme-gtk:all <none> 24.04.2-0ubuntu1
2024-07-01 22:08:17 install yaru-theme-icon:all <none> 24.04.2-0ubuntu1
2024-07-01 22:08:20 install yaru-theme-sound:all <none> 24.04.2-0ubuntu1
2024-07-01 22:08:20 install fprintd:amd64 <none> 1.94.3-1
2024-07-01 22:08:20 install libnss-sss:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:20 install libpam-fprintd:amd64 <none> 1.94.3-1
2024-07-01 22:08:20 install libpam-sss:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:20 install libsss-certmap0:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:20 install libsss-idmap0:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:20 install libsss-nss-idmap0:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:20 install python3-sss:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:20 install shotwell:amd64 <none> 0.32.6-1ubuntu1
2024-07-01 22:08:21 install sssd-common:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:21 install sssd-ad-common:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:21 install sssd-krb5-common:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:21 install sssd-ad:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:21 install sssd-ipa:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:21 install sssd-krb5:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:21 install sssd-ldap:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:21 install sssd-proxy:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-01 22:08:21 install sssd:amd64 <none> 2.9.4-1.1ubuntu6.1
2024-07-02 14:21:38 install thunderbird:amd64 2:1snap1-0ubuntu3 2:1snap1-0ubuntu3
2024-07-02 14:21:39 install dmz-cursor-theme:all <none> 0.4.5ubuntu1
2024-07-02 14:21:39 install gamemode-daemon:amd64 1.8.1-2build1 1.8.1-2build1
2024-07-02 14:21:39 install libgamemode0:amd64 <none> 1.8.1-2build1
2024-07-02 14:21:39 install libgamemodeauto0:amd64 <none> 1.8.1-2build1
2024-07-02 14:21:39 install gamemode:amd64 1.8.1-2build1 1.8.1-2build1
2024-07-02 14:21:40 install gir1.2-gnomeautoar-0.1:amd64 <none> 0.4.4-2build4
2024-07-02 14:21:40 install gir1.2-gnomedesktop-3.0:amd64 <none> 44.0-5build2
2024-07-02 14:21:40 install gnome-clocks:amd64 <none> 46.0-1build1
2024-07-02 14:21:40 install gnome-power-manager:amd64 <none> 43.0-2build2
2024-07-02 14:21:40 install gnome-shell-extension-appindicator:all <none> 58-1
2024-07-02 14:21:40 install gnome-shell-extension-desktop-icons-ng:all <none> 46+really47.0.9-1
2024-07-02 14:21:40 install gnome-shell-extension-ubuntu-dock:all <none> 90ubuntu1
2024-07-02 14:21:40 install gnome-shell-extension-ubuntu-tiling-assistant:all <none> 46-1ubuntu1
2024-07-02 14:21:41 install liblttng-ust-common1t64:amd64 <none> 2.13.7-1.1ubuntu2
2024-07-02 14:21:41 install liblttng-ust-ctl5t64:amd64 <none> 2.13.7-1.1ubuntu2
2024-07-02 14:21:41 install liblttng-ust1t64:amd64 <none> 2.13.7-1.1ubuntu2
2024-07-02 14:21:41 install libcamera0.2:amd64 <none> 0.ver2.0.r0.g89227a42-8~ubuntu24.04
2024-07-02 14:21:41 install gstreamer1.0-libcamera:amd64 <none> 0.ver2.0.r0.g89227a42-8~ubuntu24.04
2024-07-02 14:21:41 install gnome-snapshot:amd64 <none> 46.2-1ubuntu2
2024-07-02 14:21:41 install gsettings-ubuntu-schemas:all <none> 0.0.7+21.10.20210712-0ubuntu3
2024-07-02 14:21:41 install gstreamer1.0-packagekit:amd64 <none> 1.2.8-2build3
2024-07-02 14:21:41 install gtk2-engines-murrine:amd64 <none> 0.98.2-4
2024-07-02 14:21:42 install libavahi-ui-gtk3-0:amd64 <none> 0.8-13ubuntu6
2024-07-02 14:21:42 install libgamemode0:i386 <none> 1.8.1-2build1
2024-07-02 14:21:42 install libgamemodeauto0:i386 <none> 1.8.1-2build1
2024-07-02 14:21:42 install remmina-common:all <none> 1.4.35+dfsg-0ubuntu5
2024-07-02 14:21:42 install remmina:amd64 <none> 1.4.35+dfsg-0ubuntu5
2024-07-02 14:21:42 install remmina-plugin-rdp:amd64 <none> 1.4.35+dfsg-0ubuntu5
2024-07-02 14:21:42 install remmina-plugin-secret:amd64 <none> 1.4.35+dfsg-0ubuntu5
2024-07-02 14:21:42 install remmina-plugin-vnc:amd64 <none> 1.4.35+dfsg-0ubuntu5
2024-07-02 14:21:42 install shotwell-common:all 0.32.6-1ubuntu1 0.32.6-1ubuntu1
2024-07-02 14:21:43 install systemd-oomd:amd64 255.4-1ubuntu8.1 255.4-1ubuntu8.1
2024-07-02 14:21:43 install ubuntu-desktop-minimal:amd64 <none> 1.539
2024-07-02 14:21:43 install ubuntu-desktop:amd64 <none> 1.539
2024-07-02 14:21:43 install ubuntu-report:amd64 1.7.3build2 1.7.3build2
2024-07-02 14:21:43 install xcursor-themes:all 1.0.6-0ubuntu1 1.0.6-0ubuntu1
2024-07-02 14:21:43 install yaru-theme-gtk:all <none> 24.04.2-0ubuntu1
2024-07-02 14:21:44 install yaru-theme-icon:all 24.04.2-0ubuntu1 24.04.2-0ubuntu1
2024-07-02 14:21:48 install yaru-theme-sound:all <none> 24.04.2-0ubuntu1
2024-07-02 14:21:48 install shotwell:amd64 <none> 0.32.6-1ubuntu1



```

---

### Post by GogoM on 2024-07-02
I enabled Wayland and removed ubuntu-desktop and picture doesn't break now. GNOME with X11 doesn't come with a compositor anymore? But Ubuntu-desktop does?

---

