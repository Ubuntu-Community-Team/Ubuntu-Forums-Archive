---
title: "Desktop icons for all users"
date: 2006-06-18
forum: Desktop Environments
---

### Post by waster on 2006-06-18
Is there a standard gnome or ubuntu way of putting icons on each user's desktop?

I can put links in each /home/user/Desktop manually, but an "all users" desktop folder would make this easier. (Ahem, rather like Windows)

I want to do this after adding users, so adding something to the skeleton won't work.

Thanks.

---

### Post by temcat on 2006-06-18
[QUOTE=waster]Is there a standard gnome or ubuntu way of putting icons on each user's desktop?

I can put links in each /home/user/Desktop manually, but an "all users" desktop folder would make this easier. (Ahem, rather like Windows)

I want to do this after adding users, so adding something to the skeleton won't work.

Thanks.[/QUOTE]

Perhaps "sabayon" app can help you with this.

---

### Post by Ramses de Norre on 2006-06-18
You could symlink all Desktop folders to one location, but in that way all icons are the same.. I can't think of a better solution for know.

---

### Post by temcat on 2006-06-18
[QUOTE=temcat]Perhaps "sabayon" app can help you with this.[/QUOTE]

I have just checked - yes, it indeed allows you to do that.

It works like this: 

1) Install Sabayon, choose System->Administration->User profile editor. 

2) In the profile editor, click Add to add a new profile, then click Edit to edit the newly created profile. A new X session will be started in a new window inside your current session, where you can make the necessary changes. 

3) Add an icon to the desktop there in the usual fashion.

4) Click Edit->Changes to see what changes have been done. There must be only one line related to your icon; if there are many of them, put a checkmark in the Ignore column for all lines except this one. (Those additional lines in Changes In Profile window can be related to Beagle; I don't know if it is going to cause any harm if you commit them, but I unchecked them just in case.)

5) If you want to lock your icon so as to make it permanent, click on the Lock icon in this change line. "Permanent" here means that the icon will reappear upon each login of the user, even if s/he deletes it from the desktop. I also have the option Edit->Enforce Mandatory checked, though I don't know what exactly it does in addition to locking in the Changes in Profile window. You may want to investigate this.

6) Close Changes In Profile window, then choose Profile->Save in the Editing Profile window and quit this window.

7) In the User Profile Editor window, click Users and choose which users you want this profile to be applied to, then close this window.

8) Exit User Profile Editor.

---

