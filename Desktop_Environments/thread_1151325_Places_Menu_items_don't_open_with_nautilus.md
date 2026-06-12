---
title: "Places Menu items don't open with nautilus"
date: 2009-05-06
forum: Desktop Environments
---

### Post by doas777 on 2009-05-06
Update 2011-02-25:

[SIZE=2]**Solution:**[/SIZE]

there are two major solutions to this problem. The first is the easiest for novice users, so start with it:

```

1) Create a new folder on your desktop.
2) Right click the file, and select "Open with Other Application...".
3) Ensure that the "Remember this application for "Folder" files" checkbox 
at the bottom of the window is checked.
4) From the main pane, select either "Open Folder" or "File Browser"
5) Click "Open".
6) [There is NO step 6. ]("http://orangecow.org/pythonet/sketches/bruces.htm")
7) Test to make sure folders and the places menu now open with nautilus 
(the gnome file manager) correctly.
8) Delete the new folder on your deskop
9) Enjoy!

```If that does not work for you, then you will have to manually remove the association from your user profile. when this thread started, there was a bug with the Open With... applet, which prevented us from using the process above. that issue appears to be fixed in modern versions of ubuntu, but every once in a while, it's still required.

```

1) Navigate to and open ~/.local/share/applications/mimeapps.list with 
the text editor of your choice. if this file does not exist, see below.
2) locate the line that starts with "inode/directory="
3) Delete the rest of the line, and add "nautilus-folder-handler.desktop;"
4) Save and close the file.
5) Test to make sure everything works as expected.

```Since this thread started, some users have reported that the mimeapps.lst file is not where they expect it.
To find the cuplrit initially, [gasco]("http://ubuntuforums.org/member.php?u=853295") uninstalled the app that was giving him problems, and then scanned his home directory to find any references to the application.
here is he command he used:
```

find . -name '*' -print0 | xargs -t -0 grep -l <Application Name>

```this approach should allow you to find the problem even if ubuntu changes the way it stores file-> app associations.

Hope that Helps

---

### Post by doas777 on 2009-05-06
Places Menu items don't open with nautilus

My Places Menu "Desktop" and "Home Folder" and all my bookmarks open  with the Mirage image viewer instead of opening with nautilus.

Does anyone know where gnome stores it's "file type associations" for the places menu?

 Please note, this thread is a refinment of [http://ubuntuforums.org/showthread.php?t=1147873](http://ubuntuforums.org/showthread.php?t=1147873) . if an admin sees fit to delete the original, I would be much obliged.

Some Background on the issue:

I installed Mirage opened a folder of images with it, by selecting open with other application, and selecting it from the list. After that the problem began.

The Places -> Computer link, Desktop folders, and Windows opened via nautilus work just fine (but for the last, i have to get an instance of nautilus open first, which is obviously lame).

I've selected folders and told them to open with "open folder" from the "Open with Other Application" list, and even tried supplying 'nautilus' as the command, but it has no effect. 

I've seen references to an "open with..." tab in file properties, but I do not have one. likely related to this bug: [https://bugs.launchpad.net/ubuntu/+s...63/+viewstatus](https://bugs.launchpad.net/ubuntu/+s...63/+viewstatus)

If i install mirage, the problem goes away, but as soon as i reinstall it, the issue resumes.

---

### Post by s_g_robertson on 2009-05-07
I'm having a similar problem in that mine all open with VLC.  Again on 9.04(which was an upgrade from 8.04 to 8.10 to 9.04)  My desktop icons open up File Browser ok.  Strange...

Thanks
Stephen

---

### Post by doas777 on 2009-05-07
well, I gave up and installed gqview, and uninstalled mirage.

---

### Post by gasco on 2009-06-10
I had the same problem with **totem**: it opened Places menu (Documents, Music, Videos ...).

When I add a new user to test, and this user did not acquire the effect, I suspected that the problem was local to my user.

So I found the command executed (with **gnome-system-monitor**). It was [FONT=Courier New]totem-gstreamer[/FONT]

Then I typed in a terminal:
 [FONT=Courier New]$ [/FONT]find . -name '*' -print0 | xargs -t -0 grep -l totem-gstreamer

The text was find in the file:
.local/share/applications/mimeapps.list

When I opened the file, I found the next:

[Added Associations]
inode/directory=[COLOR=Red]totem-gstreamer;[/COLOR]nautilus-folder-handler.desktop;mirage.desktop;

I deleted the problematic association, and then everything was right.

---

### Post by doas777 on 2009-06-10
thank you! that is exactly the trick it would seem. and thanks for the algorithm as well. I tried searching for all files that contained mirage, but it didn't turn up anything useful. the grep must be the trick. 

thanks again,
franklin

---

### Post by unkilbeeg on 2009-06-10
This is not solely an Ubuntu problem.  I've had this problem on two of my Gentoo machines as well.  One started using Konquerer (unpleasant, but not completely ridiculous) and one started using Easytag.  Huh?

As near as I can figure out it had to do with a Gnome version upgrade, probably from 2.24 to 2.26.

I solved it by uninstalling the new "file manager" and then re-installing it.  Your way is simpler.  :)

---

### Post by gasco on 2009-06-10
you are welcome ;)
The funny thing is that the problem appeared a week ago, and googled everywhere, finding this thread.

I took the idea of adding a new user, from a problem with the other SO than only occurs with some users.

When I corrected the problem this night, first thing was to register here to share solution.

Javier

---

### Post by viuks on 2009-06-16
> **gasco said:**
> I had the same problem with **totem**: it opened Places menu (Documents, Music, Videos ...).

When I add a new user to test, and this user did not acquire the effect, I suspected that the problem was local to my user.

So I found the command executed (with **gnome-system-monitor**). It was [FONT=Courier New]totem-gstreamer[/FONT]

Then I typed in a terminal:
 [FONT=Courier New]$ [/FONT]find . -name '*' -print0 | xargs -t -0 grep -l totem-gstreamer

The text was find in the file:
.local/share/applications/mimeapps.list

When I opened the file, I found the next:

[Added Associations]
inode/directory=[COLOR=Red]totem-gstreamer;[/COLOR]nautilus-folder-handler.desktop;mirage.desktop;

I deleted the problematic association, and then everything was right.

Thank you! I had same problem, it was opening VLC on Jaunty. I just deleted mimeaps.list file, and that was all solution!

---

### Post by ogromano on 2010-01-13
Hello...

I had a similar problem... I couldn't change the preferred apps of any media files... every video and audio file wanted to open with Mplayer and every image file with EOG regardless of what changes I made with the open with or other application list. Nautilus, email and chrome were selectable from the preferred applications window and did hold when changed.

I found my .local/share/applications/mimeapps.list but I didn't have the entry you had... it looked like this... 
> 
[Added Associations]
video/x-theora+ogg=vlc.desktop;
image/jpeg=**eog.desktop**;mirage.desktop;firefox.desktop;gimp.desktop;
image/png=**eog.desktop**;firefox.desktop;mirage.desktop;gimp.desktop;
image/gif=**eog.desktop**;firefox.desktop;mirage.desktop;gimp.desktop;
x-content/video-dvd=vlc.desktop;
video/x-msvideo=**totem.desktop;**vlc.desktop;
video/x-matroska=**totem.desktop;**gnome-mplayer.desktop;mplayer.desktop;vlc.desktop;
audio/mpeg=**totem.desktop**;gnome-mplayer.desktop;vlc.desktop;mplayer.desktop;banshee-1.desktop;audacity.desktop;banshee-1-audiocd.desktop;
application/octet-stream=gedit.desktop;

My only solution was to move the apps I wanted (Mirage, Vlc, and Banshee) to the beginning of the list, saved and instantly upon right clicking on a media file I had my preferred app as the first option...

Thanks for the tip on where to look! :D

The question still remains whether this is a bug or not.

---

### Post by doas777 on 2010-01-14
there is a bug related to this iirc, but the bug centers around the inability to set/alter the association via the gui

---

### Post by ogromano on 2010-01-14
"iirc" ?

Other than it being a bug, I think that the gui is very limited. I mean how can they put "Multimedia" and expect to only use one application for all of them? There's not even a separation between Audio, Video and Pictures. I mean how do they expect Gnome MPlayer or other video app to open pictures??

---

### Post by doas777 on 2010-01-15
> **ogromano said:**
> "iirc" ?

Other than it being a bug, I think that the gui is very limited. I mean how can they put "Multimedia" and expect to only use one application for all of them? There's not even a separation between Audio, Video and Pictures. I mean how do they expect Gnome MPlayer or other video app to open pictures??

iirc => "if I recall correctly". this thread is a bit aged afterall.

---

### Post by slick1a on 2010-05-18
Hi guys and gals, 

I have the same issue as s_g_robertson ( see above)  however im unable to follow what needs to be done to correct the situation , as a result am thinking seriously about returning back to HARDY where and when everything worked as it should ~ correctly.

would some kind person be able to put in plain laymans terms how i can resolve my problem without the need to resort to hardy.

i await a speedy response..thank you in anticipation.

---

### Post by doas777 on 2010-05-18
this is a pretty old fix, so we have to hope that the mimeapps.lst file is still used in the latest versions of gnome/ubuntu. 

try this:
hit Alt + F2, to bring up the run application dialog, and paste in:
```

gedit ~/.local/share/mimeapps.list

```hopefully, gedit will open up a file with text in it. if the file is blank however, we have to go back to the beginning. let me know if that is the case, and show us a copy of the file so we can look at it. the specific issue is that folders are trying to open with vlc, correct?

---

### Post by slick1a on 2010-05-20
many thanks for the reply ~ 

yup is blank im afraid.

no furthur info unless screenshot required?

---

### Post by doas777 on 2010-05-20
well, it means that we will have to go back to the beginning

what do you get from this command:
```

find . -name '*' -print0 | xargs -t -0 grep -l vlc.desktop

```

it should list one or more files, one of which will hopefully contain the offending setting.

---

### Post by slick1a on 2010-05-20
just running cmd, v long list , so i shall just paste the important bit , cause im sure you dont want to see everything i have ... :P   biab

---

### Post by slick1a on 2010-05-20
list far to long to paste , what should i be looking for?

---

### Post by doas777 on 2010-05-21
> **slick1a said:**
> list far to long to paste , what should i be looking for?

your right, vlc is tied to everything. let me see if I can't refine the query

---

### Post by slick1a on 2010-05-21
any further updates?

---

### Post by slick1a on 2010-05-23
apt: invalid flag: get
Usage: apt <apt and javac options> <source files>
where apt options include:
  -classpath <path>          Specify where to find user class files and annotation processor factories
  -cp <path>                 Specify where to find user class files and annotation processor factories
  -d <path>                  Specify where to place processor and javac generated class files
  -s <path>                  Specify where to place processor generated source files
  -source <release>          Provide source compatibility with specified release
  -version                   Version information
  -help                      Print a synopsis of standard options; use javac -help for more options
  -X                         Print a synopsis of nonstandard options
  -J<flag>                   Pass <flag> directly to the runtime system
  -A[key[=value]]            Options to pass to annotation processors
  -nocompile                 Do not compile source files to class files
  -print                     Print out textual representation of specified types
  -factorypath <path>        Specify where to find annotation processor factories
  -factory <class>           Name of AnnotationProcessorFactory to use; bypasses default discovery process
See javac -help for information on javac options.

---

### Post by slick1a on 2010-05-23
If it helps..

on start up im asked to install fsck manually , or push the ctrl d to continue.

i have since had my window headers re-appear!!  ~ bonus there , but now i have lost audio :(

however i still have original problem of places menu opening in VLC instead of nautilus.

---

### Post by slick1a on 2010-05-23
audio has returned ~ but nautilus and vlc still not friends im afraid ...

help needed.

---

### Post by doas777 on 2010-05-24
here is a more refined copy of the find query. it will only focus on . folders, but still produces a good sized list of files.
run it on your box, and see if any of the files it suggests have names that mention mime, associations, or gnome configuration

```

find . -name '.*' -print0 | xargs -t -0 grep -l vlc.desktop

```

---

### Post by slick1a on 2010-05-25
./.gnome ./.gnome/gnome-vfs/.trash_entry_cache ./.

./.nautilus ./.profile ./.fr-sjkoIT ./.gtk-bookmarks ./

these are the only mentions i get everything else appears to be fine.

---

### Post by doas777 on 2010-05-26
> **slick1a said:**
> ./.gnome ./.gnome/gnome-vfs/.trash_entry_cache ./.

./.nautilus ./.profile ./.fr-sjkoIT ./.gtk-bookmarks ./

these are the only mentions i get everything else appears to be fine.

well, I would start in .gnome, and then .profile. 
I tried the other day to reproduce your issue and I couldn't, so could you please clarify;
when you pull down your places menu, and select 'Pictures' or whatever, it attempts to open the folder with VLC, correct?

one thing to try, is to tell it to open with another application, and select nautilus from the list, or select custom command, and enter 'nautilus'. 

also if you have a properties tab called "open with..." for folder objects

---

### Post by slick1a on 2010-06-09
I have since upgraded to karmic , this has not helped in any way , what ever i choose from my places menu opens in VLC , im also not able to burn anything to disk as this simply burns an image file.

Frankly im getting to the end of my tether here , open with is not an option as i dont know how to get there.  

left click = vlc 

right click - vlc

hardy worked fine for me , but as you do you ...one must "keep up with the jones"

any further help appreciated.

---

### Post by slick1a on 2010-06-09
by dragging my home folder to my quick launch panel right click > properties > browse   .. i can select which ever folder i choose and it opens ... problem solved.... but this is like going round me *** to get to me elbow!!

if i create another user ( which i have) all problems are resolved.

this brings me to the conclusion that somewhere along the line (since my hardy upgrade) a setting has been changed or modified.

question:  how do i find out what this change or modification is..and how do i fix it.

Short of copying many many files to my new user account i dont see my resolution in the matter of my PLACES menu opening everything with VLC.

my brain wave is to uninstal VLC.

this is what i shall try next.

---

### Post by slick1a on 2010-06-09
Ok Uninstalling VLC resolved the issue. however when i reinstalled it the problem returned.

Now i have always been a fan of vlc and i swear by it as the finest way of playing video files etc etc..

but i guess im simply going to have to do without it.

so there you go anyone having the same issue:

simply remove VLC.

Issue sort of resolved.

---

### Post by doas777 on 2010-06-11
sorry for the lack of replies. once the thread falls off the page of my last 25 posts, I kinda lose track of them. 

well, we have established that somthing has changed since we created this thread last year, because the mimeapps.list file no longer exists. 

the trick will be to uninstall vlc, and then locate all files that contain the text vlc.desktop. one of them is the cuplrit. 

now if i recall correctly, the reason we had to find the file, was because of a bug in nautilus related to the "Open With..." features. this prevented me from reseting the association just by right clicking a folder and telling it to open with nautilus. have you tried right clicking a folder, and telling it to open with 'nautilus' while the box to "remember" checked?

---

### Post by doas777 on 2010-06-16
this thread may provide some insight into the configuration of mime types and the open with menu
[http://ubuntuforums.org/showthread.php?p=2161195](http://ubuntuforums.org/showthread.php?p=2161195)

---

### Post by Muflon on 2010-06-30
I also have the same problem with VLC opening all places folders.  I have tried the default folder option but it made no difference.  My only solution has been to remove VLC.

Muflon

---

### Post by doas777 on 2010-07-01
what is the output of;
```

cat ~/.local/share/applications/mimeapps.list | grep vlc
cat  /usr/share/applications/mimeinfo.cache | grep vlc
cat /etc/gnome/defaults.list | grep vlc

```

---

### Post by Muflon on 2010-07-01
> **doas777 said:**
> what is the output of;
```

cat ~/.local/share/applications/mimeapps.list | grep vlc
cat  /usr/share/applications/mimeinfo.cache | grep vlc
cat /etc/gnome/defaults.list | grep vlc

```

cat ~/.local/share/applications/mimeapps.list | grep vlc

```
inode/directory=vlc.desktop;nautilus-folder-handler.desktop;nautilus-browser.desktop;
x-content/video-dvd=vlc.desktop;totem.desktop;
application/x-flash-video=mplayer.desktop;vlc.desktop;
video/mpeg=vlc.desktop;

```

cat  /usr/share/applications/mimeinfo.cache | grep vlc

```
 

```

cat /etc/gnome/defaults.list | grep vlc

```
 

```

Thanks

Muflon

---

### Post by Muflon on 2010-07-02
Thanks for the hint about

~/.local/share/applications/mimeapps.list 

After editing the VLC entries out of the file, specifically this one

inode/directory=vlc.desktop;

Everything is working as it should.

Muflon

---

### Post by doas777 on 2010-07-02
Great! I'm glad you got it working. sorry for the delay in responding. I'm chin deep in work work lately, and have been trying to avoid spending too much time on the forums.
I should probably take the time to clean this thread up and convert it into a how-to. 

cheers, and happy ubuntuing

---

### Post by hotdoog on 2010-08-18
:KS:KS:KS:KS:KS

This worked for me. I edited the .local/share/applications/mimeapps.list file. In my case there was a whole bunch of problematic entries listed before nautilus. Songbird, when I deleted only that it went to xmms, then baobab... I deleted all but nautilus and it finally works.

This was the useful thread for me. There are bunch of bugs about a similar but different problem out there that were no help. Other people have this problem with all nautilus "file associations" for opening a folder. I was trying that solution (right click on a folder> open with> input nautilus) in many different ways but it didn't work. The Home and Desktop links in the Places menu would still open Songbird.

I think I got this problem after upgrading from Hardy to Lucid.

I think the list of problematic file association programs included every program I have called up in nautilus to open a folder before. I don't know why it suddenly became a bug. Anyway, worked around now. Thanks.

---

### Post by P4man on 2010-10-15
Thanks for the hint about .local/share/applications/mimeapps.list !

I bumped in to the same issue with 10.10, the places menu opening those places in SMPlayer.

Is there a bug report about this? Im trying to reproduce the problem, I suspect it has something to do with opening a folder (with DVD files) in smplayer (or VLC or whatever you use), but I havent managed to reproduce it completely. Has anyone?

---

### Post by Win-Smash on 2010-10-19
> **P4man said:**
> Thanks for the hint about .local/share/applications/mimeapps.list !

I bumped in to the same issue with 10.10, the places menu opening those places in SMPlayer.

Is there a bug report about this? Im trying to reproduce the problem, I suspect it has something to do with opening a folder (with DVD files) in smplayer (or VLC or whatever you use), but I havent managed to reproduce it completely. Has anyone?

I had the same problem in 10.10 all i did to solve was to open file manager under local user (Smash) and right click on documents open with other app chose file manager :) VLC and everything opened find.

---

### Post by Win-Smash on 2010-10-20
I caused my problem using VLC player to open a DVD folder in order to play the movie. The remember this app for check box was checked.

---

### Post by P4man on 2010-10-20
> **Win-Smash said:**
> I caused my problem using VLC player to open a DVD folder in order to play the movie. The remember this app for check box was checked.

You're right. Its indeed that simple. And arguably not even a bug. After all you are instructing nautilus to open folders by default in a media player.

---

### Post by billydot on 2010-10-20
After upgrading to Ubuntu 10.10 thought everything was going smoothly until today when I now cant open any of the directories in the "Places" menu. Seems to have occured after downloading todays updates.
Sorry but linux will never catch the other 2 up as long as things like this keep happening.
Any help in words of one syllable please as I'm a newby.

---

### Post by P4man on 2010-10-20
> **billydot said:**
> After upgrading to Ubuntu 10.10 thought everything was going smoothly until today when I now cant open any of the directories in the "Places" menu. Seems to have occured after downloading todays updates.
Sorry but linux will never catch the other 2 up as long as things like this keep happening.
Any help in words of one syllable please as I'm a newby.

What happens when you try to open something from the places menu? If its the same issue we had, then do this: open a terminal (applications > accessories > terminal).

copy/paste in this command:

```
gksudo gedit ~/.local/share/applications/mimeapps.list 
```
(to paste in a terminal, use middle mouse click or shift+control+v)

A text file will open. The entry with "inode/directory"  should look like this:

```
inode/directory=nautilus-folder-handler.desktop;
```

if yours look different, post it and or replace it with mine. Save. Done.
Next time you right click something and chose "open with other application", make sure you dont keep the checkmark to always open it that app, unless you are certain :).

---

### Post by paddle on 2010-10-25
same prob

---

### Post by paddle on 2010-10-25
Thank you so much P4man done and done!!!

---

### Post by lnknpk04 on 2010-10-29
> **P4man said:**
> What happens when you try to open something from the places menu? If its the same issue we had, then do this: open a terminal (applications > accessories > terminal).

copy/paste in this command:

```
gksudo gedit ~/.local/share/applications/mimeapps.list 
```
(to paste in a terminal, use middle mouse click or shift+control+v)

A text file will open. The entry with "inode/directory"  should look like this:

```
inode/directory=nautilus-folder-handler.desktop;
```

if yours look different, post it and or replace it with mine. Save. Done.
Next time you right click something and chose "open with other application", make sure you dont keep the checkmark to always open it that app, unless you are certain :).

I will try this and appreciate your help.  However, I do want to say that your assumption is not correct - this problem occurred after an update, not after changing the 'open with' for anything.  I will correct this manually because my wife will kill me if I dont, but I would appreciate any information on submitting this as a bug so the offending update can be identified.
-------------------------EDIT-----------------------------------
Its very early and after posting I realized that this is EXACTLY something I could picture my wife doing in an attempt to listen to an entire folder of music.  I have asked her, she has admitted, and I take back my own assumption :)  Carry on...nothing to see here!

---

### Post by P4man on 2010-10-29
Well, technically its not a bug, but its certainly something that can and IMHO should be improved. Its not THAT strange to open a folder with a mediaplayer (especially if the folder contains a DVD rip) and the resulting mess is way too hard to solve.

OTOH, this is linux, so one is free to use alternative file managers and it should be possible to associate folder/inode with something else than nautilus so Im not sure what the best way would be to improve this.

---

### Post by Corrado on 2010-11-10
It may not be a bug for a media app to be the default viewer for a folder but my system was set to use the Gnome Theme Preferences panel as the default viewer.  I have no idea how that happened; I'm guessing it was during the 10.4 -> 10.10 upgrade.

Anyway, this tip helped me fix it and everything is fine now.

Thanx!
  Richard

---

### Post by endotherm on 2010-11-24
> **P4man said:**
> Well, technically its not a bug, but its certainly something that can and IMHO should be improved. Its not THAT strange to open a folder with a mediaplayer (especially if the folder contains a DVD rip) and the resulting mess is way too hard to solve.

OTOH, this is linux, so one is free to use alternative file managers and it should be possible to associate folder/inode with something else than nautilus so Im not sure what the best way would be to improve this.


the problem isn't a bug in and of itself, but in older versions of ubuntu (when this thread was created) there was a bug using the "Open With" features to fix this issue. thats why going to the mimeapps.lst manually was needed. 

now, that bug is resolved, and most users can just be instructed to right click ANY folder outside teh places menu, select "Open With Another application", and selecting "File Browser" or "Open Folder" while the "remember this setting" box is checked.

---

### Post by japglish on 2011-02-10
Thanks p4Man - it always annoys me when these things happen BUT the difference with Ubuntu is there is always a solution within reach and a decent, helpful person offering their expertise.  So unlike the nagware, virus infested mess which is Windows.  Cheers, good solution.

---

### Post by TedinOz on 2011-03-10
> **P4man said:**
> What happens when you try to open something from the places menu? If its the same issue we had, then do this: open a terminal (applications > accessories > terminal).

copy/paste in this command:

```
gksudo gedit ~/.local/share/applications/mimeapps.list 
```
(to paste in a terminal, use middle mouse click or shift+control+v)

A text file will open. The entry with "inode/directory"  should look like this:

```
inode/directory=nautilus-folder-handler.desktop;
```

if yours look different, post it and or replace it with mine. Save. Done.
Next time you right click something and chose "open with other application", make sure you dont keep the checkmark to always open it that app, unless you are certain :).

I just love Ubuntu and it's Forum assistance. I had this problem too for many weeks and after searching here found this, tried it, and it worked so perfectly! Of novices I am at the head of the list but with this support we all continue to learn.
 Thank you so much!

---

### Post by shugoshin on 2011-03-21
> **TedinOz said:**
> I just love Ubuntu and it's Forum assistance. I had this problem too for many weeks and after searching here found this, tried it, and it worked so perfectly! Of novices I am at the head of the list but with this support we all continue to learn.
 Thank you so much!


I totally agree with TedinOz and thank P4man. I have a question though: why does places not allow right mouse click? 

Also, regarding the conversation of P4man with billydot: User may change default application with right click but indeed not in places on the panel! Before this fix I could open any folder or a link to the folder with nautilus, but if I dragged that link (to that folder) to the panel it didn't open with nautilus anymore (in my case the mentioned line was changed to:
```
inode/directory=file-roller.desktop;nautilus-folder-handler.desktop;vlc.desktop;totem.desktop;
```
thus it was trying to open places with Archive Manager). I wonder how could I possible have caused this change??
 

thanks again.

---

### Post by petersicparker on 2011-05-08
Worked for me, it was that easy I couldn't figure it out myself :(

thanks!!!!

---

### Post by Jackamo1982 on 2011-06-15
Worked a treat for me, had same problem a while ago but forgot how to fix this.

Good thing there's plenty of expert help on these forums. :D

---

