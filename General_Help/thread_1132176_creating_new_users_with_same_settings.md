---
title: "creating new users with same settings"
date: 2009-04-21
forum: General Help
---

### Post by susanw on 2009-04-21
Hello,

Having installed intrepid on my partner's machine I find I now want to tweak it to get it just right for me. How do I create him his own user name which has all the settings I've set up so far to make the computer work nicely and not make me have to go through all the setting up of compiz and metacity and mouse speed etc. so it works nicely for him?

I'm happy on how to set up a user, tick different privileges etc. and I've tried saving markings in package manager and opening them on the other user but neither had the desired effect. I was wondering whether the different groups I could create would help this? Ideally I'd like an account where everything new I installed effected the other accounts but don't know if this is possible. (It's hard to keep trying different methods for doing things if you don't know that there is actually a way of doing something!)

On a slightly separate note is there a way of changing the username of the original user set up on the computer too?


Thank for reading,

Susan

---

### Post by cariboo on 2009-04-21
Go to System-->Administration-->Users & Groups, click the unlock button and enter your password. THen you can change and add/remove users.

Jim

---

### Post by stoneage on 2009-04-21
I think you can change user names following this thread here - [http://ubuntuforums.org/showthread.php?p=4968235](http://ubuntuforums.org/showthread.php?p=4968235)

Is duplicating settings as simple as copying all the .dirs from one /home to another?
You may have to change permissions once they get there but they contain all the config files and settings for most things.

---

### Post by coffeecat on 2009-04-21
As far as copying user settings and configurations is concerned, I've never done this, but this is what I'd try. You might want to create a dummy account for a dry run in case I've forgotten something and everything goes wrong. I'm assuming that the account you want to copy settings from and the account you want to copy settings to are on different machines, but the principle is the same if on the same machine.

If you look in your home folder and show hidden files (Ctrl-H in gnome) you'll see a load of folders and files beginning with a dot. These are all the gnome and app personal configurations. If you copy them as is into the second account, overwriting the original dot_files, you'll also need to change ownership with chown, otherwise the account will break. What I suggest is copying onto a FAT32 USB drive because Microsoft filesystems don't support Linux permissions and this will actually be an advantage for what I suggest you might try.

OK - log into account 1 from which you want to copy. Plug in the USB drive. Open your home folder and do a Ctrl-H. Select all the dot-files and folders and copy them onto the USB drive.

Now log into account 2 to which you want to copy and plug in the USB drive. Open the home folder and drag and drop all the dot files and folders from the USB drive into the home folder. You'll be prompted whether you want to skip or replace, so choose replace. Now log out and login again. Hopefully, all the settings will be as you want them.

However, I'm making two assumptions. First that the ownership will be changed to account 2 when you copy from the FAT32 drive. I'm 99.9% sure that will happen. Second, that the system will allow you to overwrite certain config files.

Also, one thing to watch out for. All application configurations will be transferred. This includes firefox, and bookmarks, website passwords, browsing history and cache will be transferred. If you don't want this, omit the .mozilla folder. Also, thinking of passwords, this procedure will probably transfer your keyring as well.

It needs thinking about but, as I said, this is something I've just thought up. I've never done it.

Good luck anyway.

---

### Post by susanw on 2009-04-21
> **coffeecat said:**
> 
....If you look in your home folder and show hidden files (Ctrl-H in gnome) you'll see a load of folders and files beginning with a dot. These are all the gnome and app personal configurations. If you copy them as is into the second account, overwriting the original dot_files, you'll also need to change ownership with chown, otherwise the account will break. What I suggest is copying onto a FAT32 USB drive because Microsoft filesystems don't support Linux permissions and this will actually be an advantage for what I suggest you might try.

OK - log into account 1 from which you want to copy. Plug in the USB drive. Open your home folder and do a Ctrl-H. Select all the dot-files and folders and copy them onto the USB drive.

Now log into account 2 to which you want to copy and plug in the USB drive. Open the home folder and drag and drop all the dot files and folders from the USB drive into the home folder. You'll be prompted whether you want to skip or replace, so choose replace. Now log out and login again. Hopefully, all the settings will be as you want them.


Hmm I think I'll think on that one for a bit first. 

When directories are copied (in terminal) does this mean that hidden files are not automatically copied too? Because I've just managed to create a new user, change new user to a different name and copy the home directory from the original user to the new user (with its new name). This is worked nicely but apart from being able to have the files/documents/pictures in the new user's home no settings seemed to have changed. It's saying things like I can't have desktop effects when I surely could before.

this isn't seeming that easy but I've wanted to track down where settings are stored before so that new updates could have my old settings in and maybe I'll also learn how to do that along the way.


Right  -  same problem, I still need to copy settings and am not sure that moving just the hidden files over will do it. Any other ideas welcome, else I'll try the quoted method tomorrow,

thank you

---

### Post by susanw on 2009-04-21
> **cariboo907 said:**
> Go to System-->Administration-->Users & Groups, click the unlock button and enter your password. THen you can change and add/remove users.

Jim

thank you, this is useful but the bit I don't understand in here (systems..admin..u&g) is whether adding users to groups will allow them to share settings or just files and privileges? if I knew exactly where the actual settings were stored and that creating a group with access to these would allow both (all) users to have these settings that could? be an answer.

any ideas on groups?

---

### Post by coffeecat on 2009-04-22
> **susanw said:**
> When directories are copied (in terminal) does this mean that hidden files are not automatically copied too?

No, hidden files are not copied with the 'cp' command in the terminal unless you specify something like 'cp -R ./.*' which is why I suggested using the GUI. Much easier.

Also, if you use 'cp' in the terminal you are going to end up with ownership problems and you will then have to chown. That's why I suggested using the GUI to copy to and from a Microsoft filesystem. It seems an odd thing to do but I simply offered it as a creative way of making life simpler. If you choose not to try it out, well... I can say no more. :(

> **susanw said:**
> but I've wanted to track down where settings are stored before

Settings are stored in the hidden files in the home directory - two of us have said so. The reason you haven't transferred the settings is because you haven't transferred the hidden files.

> **susanw said:**
> I still need to copy settings and am not sure that moving just the hidden files over will do it.

You could always try. :( ](*,) And since you have no faith in what I'm saying, try first using a temporary dummy account as I suggested before. That's in case your lack of faith turns out to be justified. :wink:

---

### Post by coffeecat on 2009-04-22
I thought I'd have a go at my own suggestion myself. I realised that I might find this useful to clone my personal settings from one machine to another. Goodness knows why I didn't think of this before. Anyway, I have some good news, some slightly irritating news and some bad news.

The good news:

Using an internal NTFS partition, I created a temporary folder in it and copied into this all the .folder and .file files from my $HOME folder. Then I created a new dummy account - 'bill'. Hello, Bill. I logged out and into bill and copied all the .folder and .file files from the temporary NTFS folder into bill's $HOME. BOTH TIMES USING NAUTILUS. You have to click on 'merge all' and then 'replace all'. Then I logged out and back into bill. **All my main account settings, etc have been migrated.** In fact I'm posting from the bill acount using firefox which has all my bookmarks, passwords etc.

The mildly irritating news:

When logging back into the bill account, there was an error message about wrong permissions in ~/.dmrc, but that was quickly and easily fixed, meaning that a subsequent login was uneventful. I'll leave the fix for others to work out themselves. Hint - forum search. :wink:

The bad news:

First try was to a temporary folder on an external USB drive formatted FAT32. There are a number of symlinks in some of the hidden folders. Copying to an external drive means you get warnings and these have to be skipped. This may not matter much because the warnings I got were to do with the .adobe folder (which not everyone will have) and a particular icon set which I had installed. Clearly, if you use an external drive, proceed with caution.

Final warning, **susanw**. If you do do this, **PLEASE** read what I said about firefox in my first post. If you don't omit the .mozilla folder, all your browsing history, bookmarks, cache and firefox passwords are copied. And the keyring password was copied too. That's in the .gnome2 folder (I think) but I can't be bothered to do anything about it.

---

