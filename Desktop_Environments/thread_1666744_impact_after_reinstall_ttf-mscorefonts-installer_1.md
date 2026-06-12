---
title: "impact after reinstall ttf-mscorefonts-installer 10.10"
date: 2011-01-14
forum: Desktop Environments
---

### Post by capricornday on 2011-01-14
Heloo guys, 

After install ubuntu 10.10, i want to use verdana font.
Googling for a while and i find that i must use ttf-mscorefonts-installer.
When i check to Ubuntu Software Center, the ttf-mscorefonts-installer is already installed.
So i thought that maybe i can re-install it to get the verdana font... 
Poor me.. , after remove, and re-install ttf-mscorefonts-installer, 
my desktop font is ok, 
but, my firefox, virtualbox, and thunderbird font become ugly..  

on attach 
-old.png is the firefox ubuntu at the first time (i like it very much)
-new.png is firefox now.. (ugly)

can you guys help me to bring back the ordinary font?
thank so much, and sorry for my poor english.

---

### Post by capricornday on 2011-02-26
still looking for this problem.. :(
and considering to re-install ubuntu .. phew.. :D

---

### Post by Krytarik on 2011-02-26
Enter the following command in the terminal, there might come up a dialog, if so <Tab> to <Ok> and confirm with return/enter:
```
sudo dpkg --configure -a
```

---

### Post by capricornday on 2011-03-02
Hi Krytarik,
thanks for your help..
But after i type your command in the terminal, 
after asking password, nothing happens.. :)

Do you know information or link about this..

---

### Post by walt.smith1960 on 2011-03-02
In firefox, could you do edit->preferences->content and change font selections?

---

### Post by Krytarik on 2011-03-02
Try to update your font cache, though that should have been done by the installation automatically:
```
sudo fc-cache -fv
```

**EDIT:** Forgot to answer your question, the given command would configure all downloaded/installed but not already configured packages.

---

### Post by capricornday on 2011-03-02
dear walt.smith1960
i think my problem is not only to firefox, but happen to my virtualbox and thunderbird also. but thanks for your answer :)

to Krytarik,
after i run your command, 
this is the result :

/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 44 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 32 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 1 fonts, 18 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msfont: caching, new cache contents: 31 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-droid: caching, new cache contents: 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kacst-one: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/umefont: caching, new cache contents: 18 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/capricornday/.fonts: caching, new cache contents: 2 fonts, 1 dirs
/home/capricornday/.fonts/Library: caching, new cache contents: 0 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/capricornday/.fontconfig: cleaning cache directory
fc-cache: succeeded

after that, i'm restarting ubuntu and nothing changes. 
Am i got something wrong on the report above? :)

regards
capricornday

---

### Post by Krytarik on 2011-03-02
> **capricornday said:**
> 
Am i got something wrong on the report above?
No, the output looks fine to me.

Please try fiddling with the font rendering settings "System -> Preferences -> Appearance -> Fonts -> Details...".

Also, do you have one of those files in your home directory?:
- ".font"
- ".font.conf" 
- ".gtkrc-2.0"

I would also try to re-nstall the regarding package:
```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

---

### Post by capricornday on 2011-03-02
My font setting is on attached.

in my home directory , i dont have this files :
- ".font"            
- ".font.conf"     
- ".gtkrc-2.0"     

but i have this :
.fonts 
-contains : Library (link) and aller_Lt.ttf

.fontconfig
-contains : 
 6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3 
... and something like that. :)

i'm sorry, i try to re-nstall the regarding package already. but nothing changes too. 

regards
ferdinand

---

### Post by Krytarik on 2011-03-03
> **capricornday said:**
> My font setting is on attached.

Do you use a LCD then? If not, change it to "Grayscale", I have that way, with my CRT.
> **capricornday said:**
> 
in my home directory , i dont have this files :
- ".font"            
- ".font.conf"     
- ".gtkrc-2.0"     

That's generally ok then.
> **capricornday said:**
> 
but i have this :
.fonts 
-contains : Library (link) and aller_Lt.ttf

I don't have those, but I don't think that it matters.
> **capricornday said:**
> 
.fontconfig
-contains : 
 6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3 
... and something like that.

I also have those, that's ok.
> **capricornday said:**
> 
i'm sorry, i try to re-nstall the regarding package already. but nothing changes too. 

I meant after your initial removal and install. Did you do that?

---

### Post by capricornday on 2011-03-06
> **Krytarik said:**
> Do you use a LCD then? If not, change it to "Grayscale", I have that way, with my CRT.

I meant after your initial removal and install. Did you do that?

I am using laptop, so i think the original setting is LCD right?. 

How did initial removal? from synaptic packages manager? i already do that. 
with "sudo apt-get remove" ? already do that ? 
and after do that, usually i try to restart ubuntu,  but nothing change.

regards

---

### Post by Krytarik on 2011-03-06
> **capricornday said:**
> I am using laptop, so i think the original setting is LCD right?. 

How did initial removal? from synaptic packages manager? i already do that. 
with "sudo apt-get remove" ? already do that ? 
and after do that, usually i try to restart ubuntu,  but nothing change.

Regarding the LCD setting: Yeah, right.

Regarding the font package: Simply re-install it by running the previously mentioned command, just to be sure.

---

### Post by capricornday on 2011-03-10
Dear Krytarik,
I already did your previously command to re-install ttf-mscorefonts-installer,
but nothing changes. Still looking for this issue. :( Thank u.

---

### Post by Krytarik on 2011-03-10
Does this issue only exist with Firefox?

If so, try Firefox with a fresh user profile, therefore rename the directory of your user profile: "~/.mozilla/firefox/*.default".

If that doesn't help, try removing the files in "~/.fontconfig".

---

### Post by capricornday on 2011-03-15
> Does this issue only exist with Firefox?on my first post, i told that
this happen to thunderbird, firefox, virtualbox, and i feel little bit strange about font on my wine application.  simple but annoying :D

> If that doesn't help, try removing the files in "~/.fontconfig". after removing files, restart and nothing change.

> If so, try Firefox with a fresh user profile, therefore rename the directory of your user profile: "~/.mozilla/firefox/*.default".nothing changes :)

still looking for this issue.. 
thank u

---

### Post by Krytarik on 2011-03-15
> **capricornday said:**
> on my first post, i told that
this happen to thunderbird, firefox, virtualbox,
Sorry, I didn't had that in mind anymore (since this is apparently more of a long term thread ;-)), and I apparently failed to re-check your posts.

I'm curious if this would also occur in a fresh system user accout. So, if you have nothing against it, create a new user via "System -> Administration -> Users and Groups", and then log in with those.

I will also do a further research on it later.

---

### Post by Krytarik on 2011-03-18
Please also try running those command, try it before the new user thing, if you haven't done it already:
```
sudo dpkg-reconfigure fontconfig
```

---

### Post by capricornday on 2011-03-18
after i run 
sudo dpkg-reconfigure fontconfigreboot and nothing changes. :)

so, i create a new user and surprise that the font on this user is no problem :p
here i attach snapshot about the different between new user (guest) and me,
with ambiance theme and same font setting.

>  this is apparently more of a long term thread
i m sorry because  i dont want to re-install ubuntu for just like this :)

thank u

---

### Post by bobdobbs on 2011-03-18
Just got pointed to this thread.

I'm having the exact same issue.

I've tried all the commands given in the above posts, and I've had no luck.

I haven't tried running ff as a new user yet. However, if I completely remove all my profiles and start ff fresh, I still get no luck.

I get this problem with ff3.6, ff-4.0, swiftfox, midori and abrowser.

---

### Post by Krytarik on 2011-03-18
> **capricornday said:**
> 
i m sorry because  i dont want to re-install ubuntu for just like this

I understand that, I even appreciate that, because the most people simply just re-install too fast, even with the slightest issues, or when the actual solution would be eventually simple and not even hard to find.

But what I meant is that you tend to reply each time only after several days or even later. You started this thread at 14. Januar. I guess, we could have solved this issue already with a bit more effort on your side. But it's ok, I'm fine with it. It's just, because of this, I tend to losing the thread, that's all.

---

### Post by Krytarik on 2011-03-18
> **bobdobbs said:**
> However, if I completely remove all my profiles and start ff fresh, I still get no luck.

I get this problem with ff3.6, ff-4.0, swiftfox, midori and abrowser.
We have also tried this already, as you can see. But since it isn't confined to Firefox, its user profiles don't seem to matter.

---

### Post by Krytarik on 2011-03-18
Please check the options in "Appearance -> Fonts -> Details", and if changing those helps.

@capricornday: Compare the options of both user accounts.

---

### Post by Krytarik on 2011-03-18
Upon a websearch I found a bug report regarding Firefox, I guess all Mozilla apps could be affected, and a possible workaround.
[https://bugs.launchpad.net/firefox/+bug/379761/+index?comments=all](https://bugs.launchpad.net/firefox/+bug/379761/+index?comments=all)
[http://ubuntuforums.org/showthread.php?p=7544051](http://ubuntuforums.org/showthread.php?p=7544051)

@bobdobbs: You tried this already, right?

@capricornday: You may try it, after checking the aforementioned options. Also, compare the items you inspected in post #9 in both user accounts before.

---

### Post by capricornday on 2011-03-18
@Krytarik 
Thanks for your kind help. I'm sorry i can't online everyday.. :(
So if online i always see this forum. sometime make notes and try it at home.

> 
Upon a websearch I found a bug report regarding Firefox, I guess all Mozilla apps could be affected, and a possible workaround.
[https://bugs.launchpad.net/firefox/+...x?comments=all]("https://bugs.launchpad.net/firefox/+bug/379761/+index?comments=all")
[http://ubuntuforums.org/showthread.php?p=7544051](http://ubuntuforums.org/showthread.php?p=7544051)


i will check and try your suggestion, and give feed back asap.
thank you

---

### Post by bobdobbs on 2011-03-18
> **Krytarik said:**
> Please check the options in "Appearance -> Fonts -> Details", and if changing those helps.


Under KDE, I went to 'system settings' -> 'Application Appearance' -> 'Fonts'

The setting I played with was 'anti-aliasing'. 
The default was 'system settings'. 
I changed this to 'enable'.

I restarted ff.
No dice :(

---

### Post by bobdobbs on 2011-03-18
> **Krytarik said:**
> Upon a websearch I found a bug report regarding Firefox, I guess all Mozilla apps could be affected, and a possible workaround.
[https://bugs.launchpad.net/firefox/+bug/379761/+index?comments=all](https://bugs.launchpad.net/firefox/+bug/379761/+index?comments=all)
[http://ubuntuforums.org/showthread.php?p=7544051](http://ubuntuforums.org/showthread.php?p=7544051)

@bobdobbs: You tried this already, right?



Yes indeed. This is one of the solutions I tried, without a successful result.

I have since removed the config file, because posts reporting other fixes have stated that this file should be removed for other solutions to work.

---

### Post by capricornday on 2011-03-18
I follow this thread

> [http://ubuntuforums.org/showthread.php?p=7544051](http://ubuntuforums.org/showthread.php?p=7544051)and change partial the file **/home/me/.config/font-manager/local.conf**
from : 

```

 <match target="font">
  <edit mode="assign" name="rgba">
   <const>none</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hinting">
   <bool>true</bool>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hintstyle">
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>


```into this : 

```

 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>


```and boom! :D everything back to normal.
Krytrk : thanks a lot for the link. 
ubuntu rocks

---

### Post by bobdobbs on 2011-03-18
I don't have this path:
"/home/me/.config/font-manager/local.conf"

... so I tried putting your edited file into .fonts-conf instead.

ff definately responds to it: I got errors at first. 
(running ff from terminal).
The errors were related to malformed xml.
I had cut and pasted your example, leaving out the context.
For other readers of the thread, here it is in full:

> 
<?xml version="1.0"?>                                                             
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">                                          
<fontconfig>                                                                      
<match target="font">                                                             
 <edit mode="assign" name="rgba">                                                 
  <const>rgb</const>                                                              
 </edit>                                                                          
 </match>                                                                         
 <match target="font">                                                            
 <edit mode="assign" name="hinting">                                              
  <bool>true</bool>                                                               
 </edit>                                                                          
 </match>                                                                         
 <match target="font">                                                            
 <edit mode="assign" name="hintstyle">                                            
  <const>hintfull</const>                                                         
 </edit>                                                                          
 </match>                                                                         
 <match target="font">                                                            
 <edit mode="assign" name="antialias">                                            
  <bool>true</bool>                                                               
 </edit>                                                                          
 </match>                                                                         
</fontconfig> 


So, I fixed the file. FF started without xml errors.

But alas, still no luck. My fonts are still as ugly as hell.

Just out of curiousity:
When you fixed fixed the errors by editing this file, did you have to restart X first?

---

### Post by Krytarik on 2011-03-18
> **capricornday said:**
> I follow this thread

and change partial the file **/home/me/.config/font-manager/local.conf**

Honestly, I don't know where you got those path from!? ;-)
Usually, you should create/edit the file "/home/USERNAME/.fonts.conf".
Please try it there instead, would be more accurate.
But if it doesn't work that way, put it the way you had it, being pragmatic here. ;-)

@bobdobbs: You didn't mention until now that you are using KDE. The bug/workaround regards Firefox running in Gnome. Please try the new user thing. And let's move to your own running thread regarding this (different) issue.

---

### Post by bobdobbs on 2011-03-18
> **Krytarik said:**
> 
@bobdobbs: You didn't mention until now that you are using KDE. The bug/workaround regards Firefox running in Gnome. Please try the new user thing. And let's move to your own running thread regarding this (different) issue.

Apologies - I should have thought to have mentioned that I was running KDE.

However, before we move over to my existing seperate thread, are we sure that this is specifically a firefox/gnome issue?

I'm also having the problem with chrome. The problem exists under both KDE and gnome. The thread topic doesn't distinguish between browsers and desktop environments.
Also, the solution that worked for one user on this thread was resetting font settings that should effect kde or gnome.

However, if you say so, I'm happy to move this part of the conversation over to the other thread.

---

### Post by Krytarik on 2011-03-18
> **bobdobbs said:**
> 
are we sure that this is specifically a firefox/gnome issue?

At least this is my quick conclusion after reading the bug report/comments and the mentioned thread, however I'm not really sure right now. But what I basically want to avoid, is to mingle different desktop environment in a single thread, that would become very confusing, not at least for anyone reading the thread after us.

@capricornday: [http://ubuntuforums.org/showthread.php?t=1709286](http://ubuntuforums.org/showthread.php?t=1709286)

---

### Post by capricornday on 2011-03-18
> 
Honestly, I don't know where you got those path from!? :wink:
Usually, you should create/edit the file "/home/USERNAME/.fonts.conf".
when i saw the file,  it say : 

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!--
    This file is maintained by Font Manager.

    If you wish to make any changes it is suggested you do so using

        /home/USERNAME/.config/font-manager/local.conf

    Any changes made to this file will be automatically relocated there
    at startup and any settings already in that file will be overwritten.
-->
......

</fontconfig>

```so i make the changes at there. :)
thanks

---

### Post by Krytarik on 2011-03-18
Ok, interesting! I don't have a "~/.fonts.conf", thus I didn't see that.

Btw., how about your Wine apps, do they look different in both user accounts?

---

### Post by capricornday on 2011-03-19
> 
Btw., how about your Wine apps, do they look different in both user accounts?

I try to look both of them carefully, i think they are the same. 

But hey, i tried to delete /home/USERNAME/.fonts.conf (with backup first, of course),
and give me the good font too (maybe this is only works on my case.) 
And for my curious, i look to the NEWUSER , 
and surprise that there is no /home/NEWUSER/.fonts.conf there.. :)

Do you know when this file created ?

---

### Post by Krytarik on 2011-03-19
Hey, all of the time I took into account that you stated in post #9 that you don't have that file in your home directory, but upon re-checking these posts I see that I stated the file name as ".font.conf", not ".fonts.conf". OMG, we could have solved this much earlier. But we share the responsibility for that. ;-)

And yes, the file apparently doesn't get created by default, since, like I stated (this time for real), I also don't have it in my home directory.

---

### Post by flemur13013 on 2011-03-19
After fiddling with MS fonts (and maybe before...), with ubuntu 10.04, my smaller fonts in FF4 were not 'smoothed' regardless of the font-smoothing settings set w/the GUI; I cured that by adding the below to the end of /home/name/.fonts.conf : 

 <match target="font">
 <edit mode="assign" name="autohint">
 <bool>true</bool>
 </edit>
 </match>

---

