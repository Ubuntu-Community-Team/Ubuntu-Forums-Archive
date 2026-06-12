---
title: "Desktop lockdown (Solved)"
date: 2014-08-01
forum: Desktop Environments
---

### Post by unknown6 on 2014-08-01
For some office computers we need to lock down the environment. In the past we used Sabayon to lockdown desktops, but this tool (and tools like pessulus) are not available for Ubuntu 14.04. I'm looking for a good tool to create a lockdown.

There will be two user accounts, one for a IT-manager in order to maintain the system with access to everything and a user which should only have access to a webbrowser. The user should not be able to access anything else and the browser history should be deleted when logging out.

Can someone please give me advise or tips on how to do this and which tool to user. We are currently using Ubuntu 14.04 with Gnome3, but we can switch the environment to KDE or something else.

Thank you in advance.

Update:
I managed to solve the problem

Kiosk.desktop
> 
[Desktop Entry]
Encoding=UTF-8
Name=Kiosk Mode
Comment=Kiosk
Exec=/opt/.xinitrc
Type=Application


.xinitrc
> 
matchbox-window-manager &
while true; do
    firefox
done


---

### Post by veddox on 2014-08-01
Ubuntu comes with the pre-installed "guest session" feature (at least with the Unity desktop, I don't know about the others). A user logged in as guest has no sudo privileges, and any changes he makes are automatically deleted again as soon as he logs out. For documentation, and ways to customize a guest session, see [here]("https://help.ubuntu.com/community/CustomizeGuestSession").

If that is not what you want, do a quick Google search for "ubuntu kiosk mode" or something similar. Doing that, I found one [tutorial]("http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS") that might be helpful.

Hope that helps.

---

### Post by unknown6 on 2014-08-04
Thank you for the answer. I used the Ubuntu Kiosk mode, but in combination with Firefox.
This made a good lockdown by only displaying Firefox and nothing else.

---

### Post by unknown6 on 2014-09-24
I have tested the lockdown some more, and I have encountered a problem.

Im using the following file in /usr/share/xsessions

> [Desktop Entry]
Encoding=UTF-8
Name=Kiosk Mode
Comment=Firefox Kiosk Mode
Exec=Exec=/usr/bin/firefox -height 900 -width 1440
Type=Application

Firefox opens correctly. I don't know how or why, but the menu items cannot be clicked, still be opened with shortcuts on keyboard. But this is not the biggest problem.
The users need to navigate to a certain site on which there are dropdown menu's. Just like users cannot open the menu of Firefox, they cannot open the dropdown menu on the site. They can only navigate through it with the arrows.

Can someone please help me to find out where it is going wrong?

Thank you in advance.

---

