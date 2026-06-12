---
title: "Disable Remove from Right Click Options"
date: 2010-01-06
forum: Desktop Environments
---

### Post by gnunoob on 2010-01-06
I have 9.10 running the netbook remix in a lab environment at the high school where I work. There is an account for me and an account for the students. It is very easy for them to just right click and remove all of the icons off of the menu and it's starting to get a little bit annoying. I have tried to create the account as an unprivileged user and there is no option to keep them from doing this.

 Is there a way to disable the remove options when they right click on the icon or to lock down the menu so that it cannot be changed?

---

### Post by adam814 on 2010-01-06
Give them individual accounts, that way they can only remove them for themselves and then let them deal with the consequences.:P

---

### Post by gnunoob on 2010-01-06
Thanks for the advice. That had crossed my mind but I don't think that's really an option. That would mean I would have export the list from active directory and try to figure out how to import the list of kids into all 25 of these netbooks. Thats 1149 accounts lol I would love to authenticate their initial logon through active directory but I don't know if that's possible. 

Any other ideas of how I can go about keeping the menus from being changed?

---

### Post by adam814 on 2010-01-06
Hmm...if you're going to use the same account for all the students you could configure it how you want it then back up the /home/<student user>/.config directory to somewhere they have read-only permissions.  You could write a really simple shell script like this:
```
#!/bin/sh
rm -rf ~/.config
cp -R /etc/userconfig ~/.config
```Then log in as the student user and go to System > Preferences > Startup Applications and set the script to run on login.  It won't keep them from removing things, but it'll keep them from staying that way.

---

### Post by gnunoob on 2010-01-06
that is a great idea. im guessing /etc/userconfig is the path to where i place the backup config folder?

---

### Post by adam814 on 2010-01-06
Yeah, it's just a suggestion though.  You could put it anywhere you want for that matter, it's just where it would make sense for me personally.

Make sure the student account doesn't own it and can't delete the backup.  I'd do it this way:
```
sudo chown -R root:root /etc/userconfig
```

---

### Post by gnunoob on 2010-01-06
The best thing about Linux in a school system is you can use their ignorance against them as a security measure. They'll never think to go find that folder and delete anything so I don't think we'll have a problem there. But just to be sure I will do as you say. I'm about write this up and give it a shot.

---

### Post by gnunoob on 2010-01-06
do i need to save the script file as .sh?

---

### Post by mocoloco on 2010-01-06
There are ways to [lockdown Gnome]("http://library.gnome.org/admin/deployment-guide/"), you can lock changes to the panels and whether someone can logout or restart, etc. I would imagine that similar options are available for UNR.

In Gnome the menu editor is an application called alacarte.  Not sure if it's the same in UNR but if it is you can remove it to prevent changing the menus.

---

### Post by adam814 on 2010-01-06
You don't have to save it as .sh, it's just a convention.  You do have to make it executable though.

---

### Post by gnunoob on 2010-01-06
that is what i had wrong. was not executable. thank you for your help. lets see these little demons try to play their little halo game now :) you have done a very good thing for our school i can't thank you enough for your time.

---

### Post by mcduck on 2010-01-06
Pretty much every feature of Gnome can be locked down (without changing any file permissions or doing other hacks suggested in this thread). The lockdown options are available in gconf, and if you need a GUI tool (other than the Gconf Editor) for the task then you should try Pessulus (lockdown
n editor for Gnome) and perhaps also Sabayon (user interface editor).

What comes to panel settings and menu, the relevant gconf key is **apps/panel/lobal/locked_down**. Just enable that and all panel & menu configuration options disappear.

If you are worried that some user might be aware of gconf editor and be able to disable this setting, you can run gconf editor as root (with gksudo, of course) and set the key value as mandatory.

You might also want to look at the options available under **desktop/gnome/lockdown**, they allow stuff like disabling command-line, user switching or saving data to disk. And of course any other application setting stored in gconf can be locked down as well by setting the value as mandatory.

---

### Post by gnunoob on 2010-01-15
Thanks for the reply mcduck. I am going to have to redo my image for various reasons. I will give that a shot and see what it's like.

---

