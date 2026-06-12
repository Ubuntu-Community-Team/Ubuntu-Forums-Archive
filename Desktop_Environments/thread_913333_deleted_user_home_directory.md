---
title: "deleted user home directory"
date: 2008-09-07
forum: Desktop Environments
---

### Post by Hagar55 on 2008-09-07
I deleted a use I created and then later found out that the home directory is still in the file system.
But everything in there is no use to me because I don't have the right permissions. Neither can I recreate the use for Ubuntu says the home directory already exists.
Is there a way  to change the permissions on the files ?

---

### Post by Pelham123 on 2008-09-08
If there are any files in that user account that I would like, I would move them into a separate folder in my home directory, then change the permissions. You would have to use the terminal as root and command 'mv' to move the files and 'chmod' to change the permissions.

To delete a user, as I'm sure you have realised now, you also have to delete their home folder by using this command...

sudo rm -r /home/<username>/

---

### Post by Hagar55 on 2008-09-08
I thought Ubuntu would delete everything with the account....my mistake

---

### Post by skullmunky on 2008-09-11
to change the permissions: (my username is skullmunky, the deleted one is, let's say, "joe"):

sudo chown -R skullmunky:skullmunky /home/joe

that changes the owner of the whole directory and everything in it (-R is recursive) to me.

then you can copy it all over and delete it.

btw in the Admin control panel to delete a user, there should be a checkbox to delete the home directory as well.

---

### Post by vwxy155 on 2008-09-11
Identify the small things in life that make you feel good, and do one daily. A short walk, a few minutes of writing in your journal, a short meditation, watching the sunset&#8230;whatever, will improve your outlook on life. We provide a cheap [wow powerlevel](http://www.wowgold800.com/) service for any [power leveling](http://www.wowgold800.com/) (wow leveling 1 70). [Wow gold](http://www.wowgold1000.com) here!Welcome to buy cheap wow gold! The price of [wow powerleveling](http://www.wowgold1000.com/wow-power-leveling.html) for the two new races is as the same as the original races. We are sure that you will get a satisfaction with our outstanding [world of warcraft powerleveling](http://www.wowgold800.com/) service.Blizzard Entertainment made sure that the second information film in world of warcraft, "Wrath of the Lich King" will come into the market in the fourth quarter this year, that is to say, from Oct. to Dec.

---

