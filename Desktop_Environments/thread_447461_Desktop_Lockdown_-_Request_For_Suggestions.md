---
title: "Desktop Lockdown - Request For Suggestions"
date: 2007-05-18
forum: Desktop Environments
---

### Post by knorr.orange on 2007-05-18
Soon I plan to deploy Ubuntu on about 20 school desktops to replace Windows.  I want to have the ability to lock down the desktops to restrict any action outside of running the few programs the students are to learn (TuxTyping, OpenOffice, FireFox.)

The students should not be able to move toolbars, add things to them, change background, change screensaver, save outside of specified directory, etc.  ....I think you get an idea of what I want to do here.

I have seen pessulus, the Gnome lockdown application but it still does not seem to cover everything.  As a backup plan, I will write a script to just overwrite the home directory with a standard configuration, which will run when the computer is booted.

I am requesting that people post various ideas and methods to accomplish this so I can prevent the students from making a disaster of the computers here.

Please let me know what you think!

---

### Post by dfreer on 2007-05-18
hmmm. as long as you don't grant them any sudo powers and give them each their own login, why not let them move toolbars around change desktops? if something goes wrong ("I can't find my toolbars!!") you could always delete their home directory and give them a new one. but that's just a question, that's the way you want to do things you have your reasons. 

you could try by making the appropriate files in the home directories writable only by root (chown root:root), that way the configuration of the background/toolbars can't be changed because they can't write to the files. in fact, then you could just create one folder that they CAN write to and change everything else that it is safe to change. just make sure to make normal users out of them all.

---

### Post by KillerKiwi on 2007-05-18
I think what you are after is Pessulus

It allows you to lock down anything using gconf (including panels and desktops etc).

---

### Post by rillip on 2007-05-18
Hrm.... the only way I can think to do this would be a pain in the butt, but might work.

So.  You don't want them to be able to do anything but run the apps you specify.  If we stop them from writing or executing any files but those you specify, seems like we should be covered.  If you can't modify the files, you can't make changes.

I would create a students group.  I would specify the group not have any write or execute permissions for root and all its subfolders (r-- ) .  Then you can go to specific application folders and on those specific folders give them execute permission.  Some of them might need write, for things like bookmarking in Firefox.  I guess if you're not too worried about them buggering your apps, you could give them rwx on the app folders.

Then I'd set each home directory to rwx for that user.

I think the effect of this should be to make it so that they can only read files except the apps you specify and their home folder.

I'm not 100% sure what happens if you use a gui interface and move the taskbar or something like that.  You might have to rely on Pessulus or do something drastic like chattr specific configuration files. But it'd be a pain in the butt to try and chattr every file that's used by a configuration.  I believe very bad things would happen to your system if you tried to chattr everything and then unchattr as needed... I really wouldn't recommend that.

---

### Post by knorr.orange on 2007-05-18
On the question from dfreer regarding each student having their own user account... you are correct, however I should have stated that these are students (total potential user group of 1000 different students) who have never used a computer before, So the concept of logging in and out is not likely to stick yet.  Additionally, for them to remember a password is equally unlikely.  I agree that it is the right thing to do, but the reality of the situation is that it won't work for our situation.

The idea to make everything read-only does sound like an interesting option that might work very well.  Although, I'll have to see how Gnome behaves when it can't write preferences and such.  If it can gracefully handle it rather than throw errors everywhere that could work out really well.

About the idea of students changing up settings on applications, actually I am concerned with that as well.  The problem is that when one kid goes nuts randomly clicking, and then the next kid later in the day wants to use OpenOffice, all the buttons and toolbars are different and they don't understand.

I know it sounds like I'm being a jerk restricting everything, but the sole purpose to it is to maintain a consistent experience to a large user group who has never used a computer before.  A lot of the students don't fully grasp the idea that both the monitor and computer should be turned on to get started.  So the last thing they need is for everything to look different each time they give it a try.

Thanks for the suggestions so far, please keep 'em coming!

---

### Post by dfreer on 2007-05-18
Hmmm. Sounds like making everything read only (other than the absolutely essential files needed to login/run), and only allowing them to execute specific apps would be your best bet.

You'll need to either deny access to the shell or create an extremely restictive one for the user account (think rssh only different), and chrooting them would be a great idea. 

So basically this is going to be more like an internet cafe than your typically student computers, right? because if it is going to be used for homework/assignments, you're for sure going to need user accounts. 
Why? because they'll need to save their files to something (exception here is letting them burn to CD/write to floppy/USB sticks, then I guess it would be ok), and guranteed you'll have one smartass kid that will go in and delete/corrupt everyone else's data.

EDIT: actually chroot jails with restricted shell access would be great, because then you are only including the files absolutely needed to run/login, and you can add apps and programs as needed rather than going through and trying to deny access to apps they don't need (think whitelist/blacklist). Also, I'm pretty sure you can let users login with just their name, no passwords if you think they can't remember them. Really though kids should be able to remember their last names/phone numbers/ street addresses and you could use these as passwords (login with their first & last name, and use last 4 digits of telephone number as a password). really simple stuff and if you are using chroot you shouldn't need to worry about the security risk of easily guessed passwords.

---

### Post by Mithrilhall on 2007-05-18
Deep Freeze for Linux is coming - [http://www.faronics.com/html/DFLinux.asp](http://www.faronics.com/html/DFLinux.asp)

If you search around you can find how to do the same thing on Linux that Deep Freeze does.

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux)

---

### Post by dfreer on 2007-05-18
I remember deep freeze!! and I remember my sys admin at school assuming we didn't know the escape key sequence, or how to use bootable knoppix CD's :D

---

### Post by knorr.orange on 2007-05-21
So I have done a bunch of testing to see how different things work and here's what I think I will end up going with:

I will use Pessulus to lock things down as much as I can, and then use the gnome menu editor to remove all applications except OpenOffice, Firefox, and TuxType.  The same will be done for the System menu.

For settings for the applications available, I will use a script, which will execute on login, to whack the settings directories and replace them with a standard setup.  This will be a nice change from the crazy batch file I currently have to run to modify registry settings for the Windows/Office setup.

To prevent people from putting things on the desktop, I will just make it read-only, which of course someone could change, but I don't see that happening, and I'll probably include it in the script to clean up directories.

One question though:  Is it possible to remove the "Change Desktop Background" option from the right-click menu on the desktop?

EDIT:
Found answer to the background question.... just run gconf-editor and it's under /desktop/gnome/background and then just right-click on the key for picture filename and click "Set as Mandatory"

---

### Post by knorr.orange on 2007-05-21
For anyone else following this thread looking for information on the subject, I also found the following Google summer of code project:
[http://code.google.com/soc/gnome/appinfo.html?csaid=5B80702342ED312C](http://code.google.com/soc/gnome/appinfo.html?csaid=5B80702342ED312C)

It makes a reference to the Sabayon tool for creating profiles, which is somewhat related to this thread.  If you're interested:
[http://www.gnome.org/projects/sabayon/](http://www.gnome.org/projects/sabayon/)

---

### Post by knorr.orange on 2007-05-21
For anyone following this thread looking to do the same....   I have found another method to remove applications and actions from the Gnome menus.  Go to this directory and start removing stuff:
/usr/share/applications

This will impact everyone of course, but if that works (which it does for me) then it can prove helpful.  I found this because I needed to remove things from the "Places" menu.

---

### Post by dfreer on 2007-05-21
Sounds like a start. but you will still need to limit users to not be able to use sudo (the default ubuntu login permits it) and disable any terminal/shell access. Also make sure to physically secure the computers (disable any boot up besides HD in BIOS, change the BIOS password, lock the case so that they can't be messing around with stuff (hint: CMOS battery)).

Not exactly sure how much the Pessulus tool locks stuff down, you might have already covered most of this stuff already.

---

### Post by hsweet on 2007-05-21
Browser prefs is another point. I finally got firefox prefs set in Gnome.  The key file is /usr/libfirefox.cfg.

Unchanged, it looks like this.

```
//
lockPref("app.update.enabled", false);
```

If you type ```
about:config
``` in the firefox address bar, you can see all the config settings.  Add a lockpref line for each setting you want to disable (proxy settings, home page, whatever)  Oh yeah.. back up the original first in case you screw the thing up.

That was all I had to do.  It immediatly overrode any settings my kids made.

2.. This would be a great subject to continue, maybe write a short guide for school admins.

---

### Post by knorr.orange on 2007-05-22
To address the sudo point, the plan was to make the origional installation account, but then add a second account to be used by everyone.  Then it's not on the sudo list so I should be safe there.

---

