---
title: "Changing default theme &amp; wallpaper for new users at first-ever login"
date: 2008-11-27
forum: Desktop Environments
---

### Post by narnie on 2008-11-27
I have had this issue with several installs of ubuntu followed by installing edubuntu. I have computers that I have installed in this fashion, but the adults in the house want the regular ubuntu theme for new users added to the system, not the more child-centric edubuntu theme. They would prefer not to have to change them after the first login. It is that "first impression" thing.

I have looked all over on how to change this. I have tried reinstalling ubuntu-desktop. I have edited gcong-editor as root. It still makes a new user default to the edubuntu theme. I want to make sure it is clear that I'm NOT talking about System>Preferences>Appearance and how to change it after the fact. That is simple to do.

What I'm really wanting to accomplish is changing a config file somewhere that will change the theme/wallpaper back to the normal (or even better) theme when brand new users are added to the system and they log on to Linux for the first time.

Although I am most interested for Hardy (preferring to manage LTS systems for friends and family), I had to install Intrepid on the new laptop I bought for my sister for Christmas to get the bleeding edge wireless and graphics to work correctly, so if Intrepid is different I'd like to know how to fix it there, too.

I'm facile with the command line so anything goes with the "fix."

My great thanks in advance,
Narnie

---

### Post by cdtech on 2008-11-27
Using the command:
```
sudo useradd -d /home/newuser -m newuser
sudo passwd newuser
```
I'm sure you knew this but this will create the user named newuser and give them their own home directory in /home/newuser by using the -d flag. The -m flag will force useradd to create the home directory. The files in the users home directory are copied from the **/etc/skel** folder, which contains default home directory files. If you wanted to set default values for your users, you would do so by modifying or adding files in that directory.

Hope this helps ya.....

**UPDATE::.**
By creating a testuser, setting up the user as you would want a new user to have. Copy the contents of the newuser /home directory to the /etc/skel folder then you would have the default setup for a new user that you would prefer.

---

### Post by narnie on 2008-11-27
cdtech,

Thanks for the information. That is good to know as I didn't before, however, I checked out the folder and hidden files and there are no config files for the default themes there.

What I am wanting to do is modify a config file somewhere, that, after I create a new user (your right, I knew about the useradd etc but prefer the GUI newuser tool in System>Admin> as I guess I'm lazy) and then when that new user logs on for the first time, they are presented with the desktop wallpaper and theme of MY choice, not Edubuntu's (or even Ubuntu's for that matter) choice that must be changed. I want to choose the default theme/wallpaper setup for new users.

Still, I appriciate the info as I love to learn all I can about Linux and Ubuntu.

Other thought's.

Narnie

---

### Post by cdtech on 2008-11-27
I understand. I did post an Update afterwards on how to accomplish this procedure.
> UPDATE::.
By creating a testuser, setting up the user as you would want a new user to have. Copy the contents of the newuser /home directory to the /etc/skel folder then you would have the default setup for a new user that you would prefer.
So anytime you create a new user, the default settings that you setup (from the /home/newuser, copied to the /etc/skel folder) will be applied to the new user's account.

Maybe I'm not getting what you want though.....

---

### Post by narnie on 2008-11-27
That may do it, but it is more of a work-around, than going to the source where a fresh Ubuntu install loads the human theme and background for a new user. This setting is changed when Edubuntu is installed. So, somewhere, there is a setting that says "use the human ubuntu them for the general ubuntu install" and "use the edubuntu theme for the edubuntu install."

I'd rather go to the source rather than somewhat jury-rig it.

I do like your suggestions for other things, though. I'll use it for such like base files I want a new user to be able to have access to like firefox extensions, etc. Perhaps even menu configurations.

Does anyone have any idea how Ubuntu goes about setting up a new user's theme and background if there are not config files in /etc/skel?

again, my thanks,
Narnie

---

### Post by cdtech on 2008-11-27
so you want to make your own install cd?

---

### Post by narnie on 2008-11-28
No, I don't want to maky my own install CD. Somewhere in the process of creating a new user and that user logs on, there is a config file that is read that tells what theme to use. I just want to work on that file(s). There is a config file for just about everything that happens in Linux. GUI interfaces either directly affect the config file, or are mostly front ends for command line programs that do it for these kind of things. It seems virtually everything is done from a config file. Somewhere in the change from ubuntu to edubuntu, a config file is modified to tell it what themes to use when a new user is created.

Does anyone else know where this setup is held?

Thanks,
Narnie

---

### Post by cdtech on 2008-11-28
Check out:
```
/usr/share/gconf/
```
I think this is what you want to change. I haven't read much about **schemas** but it's a start for ya...

Good luck......

---

### Post by narnie on 2009-05-30
cdtech,

Thanks so much for all that you helped me with. This was a very informative post for me. I wonder if coping these schemas from a fresh ubuntu-only install would work.

Thanks again and sorry it has taken me so long to say so,
Narnie

---

### Post by Steve N on 2010-11-03
Dredging up this old thread, I wonder if anyone has solved this problem? I've spent the better part of half a day trying to figure this one out, but no about of fiddling with files in /etc nor /usr/share/gconf will make this work.

The easiest way seems to be simply to overwrite the existing PNG file in /usr/share/backgrounds, but that's 'cheating'; there has to be a place this file is referenced to make new users see the default background.

Cheers,
    - SteveN

---

### Post by h4xor66 on 2010-11-03
i think cheating as you suggested would be the easiest thing to do, if all you need is a different default background ...... if you need a different default theme, then it's gonna get more complicated


i just thought of a way to accomplish this that isn't practical and may not work haha .... i bet someone could write a script that would monitor " users" and as soon as it detected a new user would activate a script that would automatically change that users theme and background .... ok yeah like i said , not practical :)

---

### Post by Steve N on 2010-11-03
That's probably what I'm going to do, but I am damn curious now as to where this is set, and why it ignores so many place that look logical.

Just looking at the stats on this thread (before I dredged it up), there were 9 replies and over 1800 views! Clearly a candidate for inclusion in an FAQ.

Cheers,
    - SteveN

---

### Post by mcduck on 2010-11-04
> **Steve N said:**
> Dredging up this old thread, I wonder if anyone has solved this problem? I've spent the better part of half a day trying to figure this one out, but no about of fiddling with files in /etc nor /usr/share/gconf will make this work.

The easiest way seems to be simply to overwrite the existing PNG file in /usr/share/backgrounds, but that's 'cheating'; there has to be a place this file is referenced to make new users see the default background.

Cheers,
    - SteveN

Actually the solution is already posted in this thread. :D

Just put all the relevant setting files in /etc/skel, they will be copied into every new created user's home and thus the settings are applies to that user.

The easiest way is to create a new user account, adjust all the settings as you like, and then copy the setting files from that user account's home to /etc/skel. You can of course remove the new user afterwards.

Gnome also has a GUI tool for this purpose, Sabayon, but it only helps in creating the settings and finding the relevant setting files, you still need to apply them to users manually (or using the same /etc/skel method).

edit: as a tip, the theme options, like most of the Gnome stuff, are stored in Gconf. So make sure you copy the ~/.gconf directory from your temporary account. That alone will go a very long way in customizing the settings for new users.

---

### Post by Steve N on 2010-11-04
> **mcduck said:**
> Actually the solution is already posted in this thread. :D

Just put all the relevant setting files in /etc/skel, they will be copied into every new created user's home and thus the settings are applies to that user.

The easiest way is to create a new user account, adjust all the settings as you like, and then copy the setting files from that user account's home to /etc/skel. You can of course remove the new user afterwards.

Gnome also has a GUI tool for this purpose, Sabayon, but it only helps in creating the settings and finding the relevant setting files, you still need to apply them to users manually (or using the same /etc/skel method).

edit: as a tip, the theme options, like most of the Gnome stuff, are stored in Gconf. So make sure you copy the ~/.gconf directory from your temporary account. That alone will go a very long way in customizing the settings for new users.

Yes, you're right in that I have found, in the thread, a solution to the problem, but the fundamental question remains unanswered: Where is a new users background set in an out-of-the-box setup? There are no gconf setting in /etc/skel, so when a new user is created, why does it default to the warty background? Where is *that* configured is the question.

Regards,
    - SteveN

---

### Post by mcduck on 2010-11-05
> **Steve N said:**
> Yes, you're right in that I have found, in the thread, a solution to the problem, but the fundamental question remains unanswered: Where is a new users background set in an out-of-the-box setup? There are no gconf setting in /etc/skel, so when a new user is created, why does it default to the warty background? Where is *that* configured is the question.

Regards,
    - SteveN
Like every other configuration file, gconf files sure have the "default" files somewhere in the system. Usually in /etc, so I'd place my bets on /etc/gconf... Never bothered actually looking, as there really is no reason to.

What difference does it make? You don't need to change that unless you are trying to remaster the Ubuntu CD, otherwise simply *putting* the relevant setting in /etc/skel will work just fine. Actually it would work *even* if you were remastering the CD.

---

### Post by Steve N on 2010-11-05
> **mcduck said:**
> Like every other configuration file, gconf files sure have the "default" files somewhere in the system. Usually in /etc, so I'd place my bets on /etc/gconf... Never bothered actually looking, as there really is no reason to.

Tried that. All the gnome files in /etc are empty. Also had a good look around /usr and nothing there seems to set it either. There's a link on the Gnome site on [setting look-and-feel]("http://library.gnome.org/admin/system-admin-guide/stable/gconf-9.html.en") that looks promising though, although as I mentioned, the files that they suggest changing don't contain anything at the moment. 

> **mcduck said:**
> What difference does it make? ... 

No difference. It's just a matter of curiosity and stubbornness at this point. :)

Cheers,
    - SteveN

---

### Post by mcduck on 2010-11-05
> **Steve N said:**
> Tried that. All the gnome files in /etc are empty. Also had a good look around /usr and nothing there seems to set it either. There's a link on the Gnome site on [setting look-and-feel]("http://library.gnome.org/admin/system-admin-guide/stable/gconf-9.html.en") that looks promising though, although as I mentioned, the files that they suggest changing don't contain anything at the moment. 
I'm now reading through the /etc/gconf/2/path file, which seems to contain all the info about where the settings get pulled from.

Based on that, the default settings come from /etc/gconf and  /var/lib/gconf/. You might want to check this file yourself, and also the stuff in /var/lib/gconf of course.
> **Steve N said:**
> 
No difference. It's just a matter of curiosity and stubbornness at this point. :)


That's always a good reason if you ask me. :D

---

### Post by Steve N on 2010-11-05
Mystery solved! (Thanks Mcduck)

For anyone still awake and reading this thread, here's how it appears to work:

The default background image is set in /var/lib/debian.defaults/%gconf-tree.xml

(Who would place configuration information in /var ? That's why it wasn't found earlier).

To override this, you can either change that file, or set a mandatory background in /etc/gconf. This directory is empty *until you override the /var defaults*, which you can do with this command:

gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type string \
  --set /desktop/gnome/background/picture_filename filename.png

That will set the necessary defaults in /etc/

Regards,
    - SteveN

---

