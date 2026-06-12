---
title: "Problem in playing Howzat Cricket"
date: 2010-05-17
forum: Gaming &amp; Leisure
---

### Post by binoysankar on 2010-05-17
Guys i have a problem in playing howzat cricket([www.howzat.com](www.howzat.com)). the problem is that when i login and press the "Play" tab in the browser which will show the "Select the desired minimum level of your opponent and click on 'Play Now' button". Below that there is a list box in which the type of opponents is listed, we can select any and click "Play Now", but the list box is not showing in any browsers in Ubuntu... but its working in Windows.

what could be the problem? i have reinstalled the flash player but no use...

waiting for the help


Thanks in advance...

---

### Post by Perfect Storm on 2010-05-17
I can see from the site sources that there's a lot of java involved. Make sure you have sun java installed.

---

### Post by desheikh on 2010-05-18
Hi binoysankar,

I'm the Chief developer of Howzat and this a known issue (I'm an Ubuntu user). 
The list combo box and even the friend/league listing don't appear on linux versions of flash. 
We'll be looking into resolving the issue in our next client update, but in the meantime I'm afraid you'll have to use windows :(

FYI, theres no java required on the site.

Regards,
Ali

---

### Post by binoysankar on 2010-05-18
> **desheikh said:**
> Hi binoysankar,

I'm the Chief developer of Howzat and this a known issue (I'm an Ubuntu user). 
The list combo box and even the friend/league listing don't appear on linux versions of flash. 
We'll be looking into resolving the issue in our next client update, but in the meantime I'm afraid you'll have to use windows :(

FYI, theres no java required on the site.

Regards,
Ali

oh thanks for the reply...:) i like playing howzat which is the best multiplayer online game. kudos for the work guys...:) 
i am basically a java web application developer. i have switched from windows to Ubuntu coz for its really fast and for my work/use ubuntu suits more. i also love windows too, its an awesome OS too:P... so no going back to windows now...

waiting for the updates from howzat in linux(ubuntu)...

P.S: one more feature i would like to get/add is in the "Practice mode" is to add fielders in the practice mode. currently there is only the bowler and the batsman, so while playing a lofted shot we can't judge whether the ball is played safely or not.... hope you understood it.... just a friendly suggestion don't mistake it...:)

---

### Post by errrorer on 2010-05-20
I'm not gonna switch to windows. and as, no linuxian can play howzat :(, I can't as well :(. How sad :(. Anyway, waiting for ur upgradation.............

---

### Post by arundracula on 2010-05-30
They are not going to clear this problem.. They are looking to create fancy things in their websites rather than making it playable.
Earlier it was playable. After that they modified the game and made unclickable some areas.. Then I posted this problem in planetcricket forum. After 2 days they corrected it and it was playable for atleast 2 weeks. And from then the problem has been there for now. They are not going to listen anybody. This is not an unrecoverable problem because they made it working once...

So let us stop this thing here and **don't support them if they don't support us.**

---

### Post by desheikh on 2010-05-31
Hi,

Arundracula,

On the contrary, we take user feedback very seriously, especially bug reports. As a pure ubuntu user, I don't get to play the game unless I use another machine which is quite sad :/.

I've looked into the issue and while we havn't been able to resolve it in time for our latest upload, it definitely is on our todo list. Were a pretty small team, with limited resources, so I hope you understand that fixing bugs can sometimes take some time, and we do need to prioritize them with the majority of our users in mind.
About the unclickable areas, I didn't quite get the problem your referring to, could you please elaborate?

Regards,
Ali

---

### Post by arundracula on 2010-05-31
> **desheikh said:**
> Hi,
  I didn't quite get the problem your referring to, could you please elaborate?


"The list combo box and even the friend/league listing don't appear on  linux versions of flash." Unclickable problems I've mentioned is the same issue.

---

### Post by desheikh on 2010-06-05
Guys,

While we havn't yet been able to resolve the issue for flash 10, we've found that the game works fine with the current RC of flash 10.1.

Use the following commands to upgrade:

wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc7_linux_060210.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc7_linux_060210.so.tar.gz)
tar -xvf flashplayer10_1_rc7_linux_060210.so.tar.gz
sudo mv libflashplayer.so /usr/lib/flashplugin-installer/

---

### Post by arundracula on 2010-06-07
I downloaded the flash .so file and put it manually under /opt/google/plugins and ran google chrome using the command --enable-plugins %U and it is working. Inside google chrome I disabled the old flash plugin.

So I can use the new/old plugin in google chrome and old plugin in other browsers. My old plugin is 10.0.45
[B]
But you may know, the performance of the game is very poor.[/B]

---

### Post by desheikh on 2010-06-14
The flash client for 10.1 is now in the ubuntu repos so a simple upgrade should have you ready with the new version.
Unfortunately flash performance on linux has traditionally been quite poor, we can't do much except hope that adobe picks up the pace.

---

### Post by arundracula on 2010-11-27
It is not the problem with any OS. Linux supports Flash, Mac supports Flash, Windows supports flash.

This is the problem only with the developers who are making flash content. There are numerous people who use different OSs. They have to optimize for all platforms and not like "hey I made a game, to play this you may want to install Windows"..
(Regarding howzat cricket, it was working super smooth for some months and they changed it without checking it in linux. They all know flash in linux is not h/w accelerated while developing).
I am telling this because I am a flash game developer. I've to optimize my game for all platforms.

A developer made a game which doesn't play smoothly in a flash player is not Adobe's problem.

---

