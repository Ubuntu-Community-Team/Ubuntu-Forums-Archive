---
title: "New to linux - Help!"
date: 2005-06-22
forum: Desktop Environments
---

### Post by semilemon on 2005-06-22
Hello. I've just installed Ubuntu (dual-boot, currently I'm in XP) and I have a few questions.

1) How do I set up ubuntu so I can connect to the net with my linux os?
2)The screen resolution is 640x680. This is too small. However, it is the only option on the 'screen resolution' menu. How do I change it.
3)Also, the small text of the login screen is blurry. Why is this?
4)And finally, I accidentally mis-spelled the password for the root account the first time, and so in the installation I couldn't verify it the second time, so I skipped it. However, How can I get into the 'root' accout now?

Thank-you.

---

### Post by Dave_is_sexy on 2005-06-22
Pointless reply but....

Presumably if your net's not working already you're using an external and/or dial up modem. You'll need to spec exactly what set up you have, and then someone should be able to point you to the answer quite easily.

All the monitor stuff is graphics drivers. You'll need to get new ones, although if there was nothing with ubuntu you'll struggle unless someone has already manipulated the windows driver to work and that'll be alot of text document editing.

..which you can't do without root powers. I'm not sure how you managed to do that. The account you created at start-up however, might be able to change the root password from the admin control panel > users & groups

But since you haven't done anything yet and it's totally screwed up in so many ways i'd suggest (personally) just installing it again from scratch and if that doesn't work put Mandrivia on instead. It has better out of the box support for external / usb modems, and better graphics card support than Debian (at least as of last year) which Ubuntu is based on.

..although, Ubuntu doesn't let you make a root account at the instalation satge like other distros do *raises eye brow*

---

### Post by astoltz on 2005-06-22
[QUOTE=semilemon]1) How do I set up ubuntu so I can connect to the net with my linux os?[/QUOTE] The install should have detected any network interfaces (modem, ethernet etc..).  Did you try the gnome network admin tool (click system tools -> networking)?

Both 2) and 3) sound like Ubuntu did not get the correct grahics driver installed. What graphics card do you have?
[QUOTE=semilemon]4)And finally, I accidentally mis-spelled the password for the root account the first time, and so in the installation I couldn't verify it the second time, so I skipped it. However, How can I get into the 'root' accout now?[/QUOTE]Hmmm, not sure how this happened as the Ubuntu install does not normally ask for a root password.  See [this](http://www.ubuntulinux.org/support/documentation/faq/root) for a better discussion on whats going on with the root account.  When you log in as the first user you created at install, open a shell and type ```
sudo -s
```  When prompted for a password, enter **the user's** (not root's).  Then you should have root prompt.

---

### Post by semilemon on 2005-06-22
I fixed the whole root thing by simply re-installing, since I haven't done anything anyway. I'll try getting the internet to work right away and from there I'll get new graphics drivers. Thank you for your help.

---

### Post by Zeroedout on 2005-06-22
if his resolution is stuck at 640x480, his graphic driver may be okay, it may just not be detecting the monitor refresh rates and display size. You have to open up your xorg.conf (sudo gedit /etc/X11/xorg.conf ) and add the HorizSync and VertRefresh options and probebly also the display size, maybe even higher resolutions. search the forums, you'll find countless posts about people with Intel cards and this problem. I know i had this problem on a machine with an intel i810.

---

### Post by semilemon on 2005-06-22
Me again. I've noticed you all talk about menus such as 'Networking' and 'Users and Groups'. However, whenever I try to open one of these, the "swirling circle thing" (I'm assuming it is the equivalent to the hour glass in windows), it says it is starting it up but then it never does. Any ideas with me problimatic-installation?

---

