---
title: "Can't login to desktop XFCE"
date: 2019-06-17
forum: Desktop Environments
---

### Post by jmcgee on 2019-06-17
I am on Ubuntu 18.04.2 LTS

I have been unable to login to the desktop through the desktop prompt using lightdm. If I switch it to gdm3 using sudo dpkg-reconfigure lightdm

I can login to ubuntu, but not xfce or xubuntu. 

Once in ubuntu desktop, I cannot use any app that wants to authenticate. Example when running Synaptic, I get a window titled Athentication Required. It only asks for password, I enter password for the the user logged in and it says Sorry that didn't work. From terminal, I can start synaptic using same password.

---

### Post by Artim on 2019-06-17
Are you running Xfce added to an Ubuntu install or is that Xubuntu?  Multiple desktops on the same machine used to be easy, but now there's a mix of GTK2 and 3, Qt / Plasma, and several window managers as well.  They don't all play nicely with one another.  More info is needed in order to help you.

---

### Post by jmcgee on 2019-06-18
I think Xbuntu. That is the splash screen that comes up on boot.

---

