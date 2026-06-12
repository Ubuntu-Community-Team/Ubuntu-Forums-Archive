---
title: "[SOLVED] Using Konqueror instead of Dolphin in Gutsy"
date: 2007-10-11
forum: Desktop Environments
---

### Post by eurgain on 2007-10-11
There must be a way to do it!

Dolphin is just too raw and underdeveloped to be the mainstream file manager at this stage, whereas Konqeror, as a file manager, is mature and familiar.  When KDE4 is with us, maybe Dolphin will be fine, but now is not its time!

I have grepped and grepped and just cannot find where the setting for the default KDE file manager is specified!  Can anyone help?  It is spoiling (to the point of a complete no-go) KUbuntu in the RC for me as an install once the release comes available.  (I love VMWare, for trying out new OS releases!)

A

---

### Post by auditar on 2007-10-11
eurgain,

The following seemed to work for me.

[[COLOR="Blue"]http://sathyasays.com/?p=23[/COLOR]]("http://sathyasays.com/?p=23")

---

### Post by eurgain on 2007-10-12
Spot on, thanks!

Also, thanks for the reference to [http://sathyasays.com](http://sathyasays.com) .  That is a nice site that I have not come across before, somehow.

A

---

### Post by hogman23 on 2007-10-15
Here is an easy synopsis of how to fix it.

Open Run Command
Type "kcontrol"
Expand "KDE Components"
Click on "File Associations"
Expand "Inode"
Click on "Directory"
Move Konqueror above Dolphin in the "Application Preference Order"
Click Apply

---

### Post by tubunu on 2007-10-16
Unfortunately on my system even when I moved Konqueror above Dolphin in the "Application Preference Order", and hit Apply, the default is still Dolphin. It seems as if Apply button doesn't do it. :( 

I solved it by completely uninstalling Dolphin. If anyone knows a workaround to that, share.

---

### Post by the.ant on 2007-10-18
Uninstalling worked fine for me. It's actually the first thing I did after the fresh install of Gutsy today. I nearly became mental trying to organize my files with Dolphin, it's so... useless. 
 Whoever had the idea that it would be more userfriendly than Konqueror should definetly go easier on the shrooms...

---

### Post by chemist109 on 2007-10-19
I found this post and immediately set the default back to konqueror.  Until dolphin gets a tree view, I won't even consider it as a file manager.

---

### Post by maybeway36 on 2007-10-19
Thanks so much! This was the first thing I did after instaling 7.10.

---

### Post by Akre on 2007-10-19
Thank you sooo much for this. This dolphin is too simple. I am using Kubuntu couse I do not want simple solutions !

---

### Post by fuscia on 2007-10-21
thank you. i've had enough of thunar's evil twin. made me appreciate konqueror all the more.

---

### Post by Flare183 on 2007-10-22
Yeah same here. Dolphin royally sucks. Sudo apt-get remove that! Konqureror done then rest after that!

---

### Post by luis.alves@lafaspot.com on 2007-10-24
using Dolphin on ubuntu gutsy 7.10, helped me understand that the flaws in konqueror are not as bad I used to think.
Konqueror is still the best file manager for KDE.

---

### Post by stimpack on 2007-10-25
Thanks for this.

While I don't think Dolphin sucks, far from it, it does seem to cater to a minimalism that doesn't fit well with us KDE folks. To be fair to it, they added a ton of power to it compared to other simplistic file-managers. But for me Konq is just too good not to use.

---

### Post by Vozmozno on 2007-10-26
I could have managed using Dolphin if it wasn't for the fat that it fails to create or delete files and folders on my home network.... I do this fairly often so its a big nuisance to grab 5 or six files, copy + paste and then see the "copying has failed" or some such error.... Then I'd have to go look for Konqueror and do it. Dolphin is about to be un-installed from my system, thanks for the help ¡=)

---

### Post by barney_1 on 2007-11-01
Apparently a tree view is in the works for dolphin.  The official release for KDE4 isn't until December so I'm reserving judgment to see what ships in the point release.  

I was unable to make konqueror the default file manager without uninstalling dolphin.  I'm not sure how to file a bug report, does anyone know if one has been opened?

---

### Post by explemonk on 2007-11-01
> **barney_1 said:**
> Apparently a tree view is in the works for dolphin.  The official release for KDE4 isn't until December so I'm reserving judgment to see what ships in the point release.

There is a tree view in the current KDE 4 version of Dolphin, but it is not a full file system tree view.  Rather, it is a tree view of the directory you are currently in.  It's pretty useless, if you ask me.

---

### Post by lptr on 2007-11-12
First I thought Dolphin would be number one choice instead of Konqueror. 

Today I set Konqueror back as default filemanager (as described somewhat above). 

Dolphin is perfect when I want to edit system configuration files as root. This still unsolved kdesudo issue with konqueror drove me nuts since 5.04 (Hoary). But Dolphin drives me nuts because it is not possible to switch the preview view to details view as default for all directories. Maybe it is a bug but it is not possible to store this detail view permanently.

When I opening dirs as root it does this. Most of the time I don't want to manipulate system files. So this is quite boring to manipulate permissions afterward copy or moving files.

rob*

---

### Post by trtech on 2007-11-17
Just want to chime in to say: Konqueror is the reason I use KDE. I cannot understand why anyone would decide to replace it.

---

### Post by lptr on 2007-11-17
> **trtech said:**
> Just want to chime in to say: Konqueror is the reason I use KDE. I cannot understand why anyone would decide to replace it.

Well, did you have a look at dolphine, yet? 

What I do miss in konqui is the ability to edit (system) files as root. Or simply by klicking on a button and entering my passwd changing into root context.

Yes, there is this kdesu thing, but the issues with it drove me nuts. This was the main reason why I stayed such a long time with my main machine with 5.04 (since last week). Now the new machine is up and running.

Dolphin is just another admin tool, I have to, but would not use, if Konqueror would have built in that 'run as root' button. Otherwise I agree with your oppinion: Konqui is the ++ for KDE.

rob*

---

### Post by trtech on 2007-11-17
> Well, did you have a look at dolphine, yet?

Only briefly. I had read the release notes:
[http://kubuntu.org/announcements/7.10-release.php](http://kubuntu.org/announcements/7.10-release.php)
and they say, "Dolphin is not a replacement for Konqueror as Dolphin only acts as a file manager."

At any given moment I usually have 3-5 tabs open in Konqueror, each split vertically with a remote machine on top (via SFTP) and the local working copy below.

So, yes, I looked for way to split the view top-bottom, then looked for a way to connect to an FTP server in Dolphin. Didn't find either, so I looked for a way to set the default to Konqueror, found it, did it and went back to work.

---

### Post by wolfear on 2007-11-18
Just encountered Dolphin after upgrade...it royally bites the big wazoo.
Someone was smoking some serious crack when they included that one.

Thanks for the info on how to change back to konqueror.

---

### Post by samwyse on 2007-11-18
> **explemonk said:**
> There is a tree view in the current KDE 4 version of Dolphin, but it is not a full file system tree view.  Rather, it is a tree view of the directory you are currently in.  It's pretty useless, if you ask me.
That's pretty crappy. I hope the icon spacing is configurable in the KDE4 Konqueror like in the (Gutsy) Dolphin and there's a proper tree view. Unevenly placed and too tightly positioned icons are my main annoyances with Konqueror.

edit: there was a proper tree view in kde4 beta1.

---

### Post by noyso on 2007-12-01
first af all, huge thanx for hint how to get rid of dolphin ! i've used MC and console to operate files before  this post )


> **lptr said:**
> 

Dolphin is perfect when I want to edit system configuration files as root. This still unsolved kdesudo issue with konqueror drove me nuts since 5.04 (Hoary).



check out this script:    _[COLOR="Blue"][http://www.kde-apps.org/content/show.php?content=11998](http://www.kde-apps.org/content/show.php?content=11998)[/COLOR]_

[LIST=1]
[*]unpack
[*]copy contents of "Root_Actions_2.1.1" folder to  home/USERNAME/.kde/share/apps/konqueror/servicemenus (change USERNAME to your username)
[*]check out!
[/LIST]

this script adds "**Root Actions**" submenu in konqueror's and dolphin's context menu.

available options (hang on your chair):

[LIST]
[*]Open Terminal Here (folders)
[*] Open in File Manager (folders)
[*] Open as Text (files)
[*] Open With ...
[*] Copy (both)
[*] Move/Rename
[*] Delete
[*] Ownership to Root (both)
[*] Ownership to Active User (both)
[*] Ownership to ...  (both)
[*] Change Permissions (both)
[/LIST]

enjoy!  :)

---

### Post by lptr on 2007-12-02
@noyso: With that sort of kdesu calling I had lots of trouble. Since Hoary kernel they changed something. Sometimes calling kdesu started apps and it works, but other times not. For example if you are kdesudo ing konqueror after fresh booting KDE will ask for your pswd, and Konquerer does start. Some minutes later if you want to start another kdesudo konqueror (to move around rooted files) then only icon is bumping around and nothing else does happen. I did try that stuff from shell window. Sometimes messages regarding X, sometimes regarding DCOP server. Pretty mad if you NEED to do something immediately. If you close the first rooted konquror window, and trying to reopen it as root, then you need to exit session to get it back to life. So the only way would be to start another shell window and vi, mc whatever. Really boring. 

Since Hoary I was not able anymore to predictable starting konqueror and from it to run kate or kwrite in root context. Dolphin was the first tool that reenabled me doing this. So I will using it for admin purpose in future. There is no replacement for konqueror, though. Would love to have the functionality back I had with Hoary. Seemless doing all in Konqueror. For me Dolphin is only a workaround. No permanent solution.

rob*

---

### Post by mateuszbaranski on 2008-02-11
> **trtech said:**
> Only briefly. I had read the release notes:
[http://kubuntu.org/announcements/7.10-release.php](http://kubuntu.org/announcements/7.10-release.php)
and they say, "Dolphin is not a replacement for Konqueror as Dolphin only acts as a file manager."

:lolflag:
"only acts as a file manager" - so actually it DOES replace konqueror file manager functionallity....
Every time I insert USB pendrive and this crappy Dolphin program launch I get nervous. I had to uninstall it.

---

### Post by CopaceticOpus on 2008-06-23
Thank you for the instructions on how to change back. I rely on tabs and the tree view! (FYI, this solution works in Hardy too.)

This setting shouldn't be so buried. Any time such a major change is made, you know some users won't like it, so it should be easy for them to revert. 

(This is the same mistake made with Firefox's Awesome Bar. I like it, but some people don't. If they had simply added a checkbox in the settings for "Address bar matches URLs only", we wouldn't have so many people complaining about it.)

---

