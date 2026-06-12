---
title: "Administrator mode in system settings failing; login manager issues"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Baji on 2006-06-02
My first post on this forum, i've been here for a long time and been using the wealth of information about breezy, solving about every problem I encoutered using the search function and the ubuntu wiki.

I just did a fresh dualboot install of dapper to test it out. Here are some problems I encountered . These all apply to Kubuntu, which seems to have more issues than ubuntu. 

I hope someone can help me resolve these three issues

1. While trying to change the system preferences by switching to Administrator Mode often there is no password prompt and the field remains greyed out. I have to resort to using kcontrol or sudo kcontrol.

2. I tried to get the users listed in the login manager with an picture, and show list seems to be selected by default in the configuration, but there is still a box where you have to type your name and password at the login screen.

3. There doesnt seem to be support for multiple soundcards, I have to resort to alsa tricks like pointing to a different hardware adress in amaroK (hw:1). I also used the override device location in the Soundsystem's Hardware preferences, but this doesnt seem to affect most applications. As it isn't uncommon to have two soundcards (built-in and pci for example) it should be possible to select the default soundcard (?)

thanks in advance for any help,

Pelle

---

### Post by Karlos on 2006-07-31
I just installed Kubuntu ran automatix had couple of problems with guarddog and nvidia but its all working 

except for administrator mode like yourself...

it just hangs...

---

### Post by SavageHcky7 on 2007-12-31
I have encountered a very similar problem, a year after the original post.  :(

I am using Kubuntu, 7.10, with compiz-fusion.  When I try to use K->System Settings and enable Administrator Mode, I enter my password in the dialog box, but nothing ever happens afterwards.  It happens with Display settings, User Management, anything.  

kcontrol works, using sudo.  I am a member of the admin group.

Any help would be appreciated!

---

### Post by SavageHcky7 on 2008-01-27
Anyone seen this?  I am still having this problem, and am about to do a reinstall as I cannot seem to fix it.

---

### Post by Flippy209 on 2008-02-24
I'm having the same problem. I'm trying to share files and first I couldn't use "administrator mode" to add users. So I did that through command line. Now I'm trying to share the files and "administrator mode" just sits there most of the time. Sometimes it will ask me for a password, but usually not. When it does I'm not able to edit or create a share, when it doesn't obviously I'm also unable to edit or create a share.

I tried using kcontrol. It offers the "administrator mode" button, but never allows me to actually make changes.

---

