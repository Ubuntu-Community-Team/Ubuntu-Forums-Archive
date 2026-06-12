---
title: "Im new in kubuntu and have 4 questions about kde"
date: 2007-09-15
forum: Desktop Environments
---

### Post by lllllinux on 2007-09-15
1)how i can cancel the icon of the application that popup when i click on some application ?

2)when i click on "volume +" or "volume -" on my multimedia keyobard i key a volume osd that show me the volume of the system , how i can cancel this and to increase \ decrease the volume with these keys but without the osd ?

3)in konqueror how i can view picture from the video instead of this icon ( avi,wmv,mpg work in my computer in all the player , and i have enabled all the previews in konqueror )
[IMG]http://img142.imageshack.us/img142/1656/10063414fq1.jpg[/IMG]



4)in firefox how i can view avi \ wmv \ mpg files ( not mms ) in the browser but not with mplayer and mozilla-mplayer , like in ubuntu where is automatic start when you click on the link

5)i have installed "kcontrol-autostart" and i add new application in the 3 fields i have inserted "amarok" , and when the desktop is startting i get error ( i automatic login with my default user , and im always start an "empty session" )

---

### Post by miggols99 on 2007-09-15
1: Press Alt f2. Type 'kcontrol' and press enter. Click on 'Appearance and Themes'. Then choose 'Launch Feedback'. Where it says bouncing cursor, change that to something you would like.

2: Not sure how to do this...

3: Right click desktop, then configure desktop. Click on behaviour on the side. Then click on the file icons tab. Tick Video files.

4: Not sure what you mean.

5: Could you tell us what the error says?

---

### Post by lllllinux on 2007-09-15
thanks for the replay , the first problem is fixed.

about 3 , in the menu , i have clicked "icons" tab but in this tub i have no video only pictures, pdf , koffice files , text files but not video , the same in konqeror preview i have no video and video is working well in my computer.

about 4 - i mean that you click on link to video ( but no mms ) i want it to play in the tab in the browser and i will have control keys , like it is in ubuntu ( i use firefox )

about 5 - this is the error : " the file amarok.desktop have no type= property" some close to this its translated.

and something new that i have found now , when i create text file and edit him with kate and save , it automatic create another green file in the same dir of the text file how i can cancel this ?

---

### Post by bakster on 2007-09-15
3 - install mplayer and [this]("http://xemanth.webhop.org/packages/mplayerthumbs_0.5b-1_feisty_i386.deb")  deb package and you will have nice nautilus-like video previews

---

### Post by GeneralZod on 2007-09-15
> **lllllinux said:**
> 
and something new that i have found now , when i create text file and edit him with kate and save , it automatic create another green file in the same dir of the text file how i can cancel this ?

Settings -> Configure Kate -> Open/ Save -> uncheck the "Backup on Save" check boxes.

---

### Post by lllllinux on 2007-09-15
yes its work thanks

---

### Post by kuja on 2007-09-15
not sure about #1, you worded it in a confusing way, (a guess interpretation) if you mean the little popup when you hover over tray icons, you can disable that can be altered from here: right click the panel, configure panel, appearance

not sure about #2 either ... I perhaps foolishly believed that the laptop was doing that :s

3: installing the kdemultimedia package should help

4: No idea, I don't like to stray far from my KDE :)

5: What error?

---

### Post by Brian96 on 2007-09-15
I'm not sure, but #4 could be because Ubuntu uses Totem as its default video player (and possibly also for Mozilla plugins?) and KDE uses something else. Not sure what the solution would be, but I know in my customized Gnome setup, VLC is my only media player, so all video links play full screen in a tab in my browser (but without controls, unfortunately).

---

### Post by lllllinux on 2007-09-15
ok i have fixed some problem and this is what i still need to fix :

1)when i start kde i get error " the file amarok.desktop have no type= property" from kcontrol-autostart

2)how i can set to "view" in konqueror for every folder something else (and not global) for example i have folder with alots of song and i wint to view it on "list" and other folder have only two text files so i want to view it as "icon" how i can do it ?

3)when i click on "volume +" or "volume -" on my multimedia keyobard i key a volume osd that show me the volume of the system , how i can cancel this and to increase \ decrease the volume with these keys but without the osd ?

4)when i start konqueror its start a bule page with option , how i can change the default page and choose the page that it will start with ?

5)the firefox \ totem video problem

6)why kmix doesnt start when kde start any more ? maybe i did somthing but i dont remember how i can set it to start when the system start again ?

Sorry about these many questions

by the way the kdemultimedia is perfect its what i have looked for.

---

### Post by kuja on 2007-09-15
b4) Just change your homepage in settings-> configure konqueror -> Behavior
b6) 2 easy ways to change this, the first would be to go to system settings -> advanced -> session manager and change it from restore previous session to restore manually saved session, get things the way you want, then go to kmenu -> save session. The other way would be to add a launcher for it in ~/.kde/Autostart

---

### Post by lllllinux on 2007-09-16
in konqueror i have changed in  settings-> configure konqueror -> Behavior the address
but still when i run konqeror i start with the "Welcome to konqeror" page

---

### Post by kuja on 2007-09-16
hmm, try setting it to your home directory, then going to settings -> save view provile "File Management", close out all instances of konqueror, and reopen konqueror and see if it'll do the trick.

---

### Post by lllllinux on 2007-09-16
> **kuja said:**
> hmm, try setting it to your home directory, then going to settings -> save view provile "File Management", close out all instances of konqueror, and reopen konqueror and see if it'll do the trick.
its working thanks

how i can clear all the command that i did in alt + f2 ?

how i can make konqueror not to use what i set in "view" as global but only for the dir that i have set in

---

### Post by GeneralZod on 2007-09-16
> **lllllinux said:**
> its working thanks

how i can clear all the command that i did in alt + f2 ?


Alt+F2, right-click on text box, "Clear History"

> 
how i can make konqueror not to use what i set in "view" as global but only for the dir that i have set in

Ordinarily, Konqueror has a setting in the Settings menu called "Save View Changes per Folder", but Kubuntu removes this *sigh*

I'm not sure if there's an elegant solution, but I always just follow the steps here:

[http://www.kubuntu.org/faq.php#konqueror](http://www.kubuntu.org/faq.php#konqueror)

---

### Post by lllllinux on 2007-09-16
both didnt work for me  , when i try "Clear History" i get "cant run this command"
and in this link there are only how to return to the default profile , any ideas how to these things ?

---

### Post by kuja on 2007-09-16
Returning to the kde profile (as opposed to kubuntu's "simplified" (read as: crippled)  profile) is what you need to do to get the "save view changes per folder" option in the menu (among other things). Following the instructions on the link general zod gave you may work. (I used [http://jucato.org/kde/konq-profiles.html](http://jucato.org/kde/konq-profiles.html))

To clear the run command history, right click on the text-box and click "clear history"

---

### Post by lllllinux on 2007-09-16
> **kuja said:**
> Returning to the kde profile (as opposed to kubuntu's "simplified" (read as: crippled)  profile) is what you need to do to get the "save view changes per folder" option in the menu (among other things). Following the instructions on the link general zod gave you may work. (I used [http://jucato.org/kde/konq-profiles.html](http://jucato.org/kde/konq-profiles.html))

To clear the run command history, right click on the text-box and click "clear history"
this history clear is perfect i dont know how i havent thought about this before , and about the second i have returned to the default profile but i still dont find the "save view changes per folder" option where it is ?

---

### Post by kuja on 2007-09-16
> **lllllinux said:**
> this history clear is perfect i dont know how i havent thought about this before , and about the second i have returned to the default profile but i still dont find the "save view changes per folder" option where it is ?

should be in the "settings" menu.

---

### Post by lllllinux on 2007-09-16
ooops my mistake i have it thanks all

---

