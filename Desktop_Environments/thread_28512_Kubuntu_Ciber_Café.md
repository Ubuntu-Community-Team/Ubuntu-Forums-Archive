---
title: "Kubuntu Ciber Café"
date: 2005-04-20
forum: Desktop Environments
---

### Post by Rodrigo on 2005-04-20
Hello Happy Kubuntu Users.
Im a Ciber Cafe Owner, and I had (still have in one) WinXP on my PC's
But as U guess, They are NOT Legal HAHAHA. Therefore I have to make a migration to make my life easy and be able to sleep at night  :) , and Im loving it.
I LOVE Kubuntu, I use ubuntu and Slackware in my home, but KDE its more intuitive and works like Win so users find it a lot easy, that's why I use Kubuntu. I send to hell win last Sunday, and I start learning to use apt-get (becouse I dont have Internet on my house) send to hell kopete, installed Gaim, and FireFox, but I want to install kde spanish lang, and I have no idea how to... so... 
My first Question is:
    How do I install Spanish Lang to Kde?
    (and how to do the same with OpenOffice, with the dictionaries and all?)


Ok, now, when I used Win, I have a Shared Unit (Music) so my costumers would lisent to the music I had in there (becouse I dont like them to download music, eats my bandwith)
so... My next Question is:

    WICH method its better (use SMB or Shared Public Server or any other) or use when you want to share a folder over a network???

Thats all for the moment  :smile: , and one more thing, you dont have to give me a full detailed answer, I want to learn, so weblinks will do, but if you incist  :wink:

---

### Post by pomalin on 2005-04-20
sudo apt-get install kde-i18n-es

or search kde-i18n-es in kynaptic

after that kde control center, and add spanish, and that's all I think.....

for open office it's openoffice.org-l10n-es

---

### Post by philipacamaniac on 2005-04-20
Not exactly sure what you are asking with your network question, but Samba (SMB) is fairly universal now, and can be accessed by Windows, Linux and Mac clients.

Also, I don't know if the kde-i18n-es takes care of OpenOffice.org and other GNOME apps... can someone confirm?

---

### Post by Seth on 2005-04-20
Just install the metapackage **language-support-es** and it will set up OpenOffice.org, Firefox, etc.! :D

Then install **kde-i18n-es** for KDE.

---

### Post by Rodrigo on 2005-04-20
thank you all for your help!  :grin: , I got another Question:
    Since I have 6 pc's, I dont want to download the same packages for all, its a waste of time, so..
    How can I use the same packages I donwload for 1 pc and use them in all the others?

---

### Post by lateo on 2005-06-03
you might set up a local mirror.
you might have a look at 
[http://www.interparse.com/debianmirror/](http://www.interparse.com/debianmirror/)  (en)
[http://www.debian.org/mirror/ftpmirror.fr.html](http://www.debian.org/mirror/ftpmirror.fr.html) (fr)
could not find back the one i think's really good :.(

---

### Post by jeremy on 2005-06-04
[QUOTE=Rodrigo]thank you all for your help!  :grin: , I got another Question:
    Since I have 6 pc's, I dont want to download the same packages for all, its a waste of time, so..
    How can I use the same packages I donwload for 1 pc and use them in all the others?[/QUOTE]
 If your pc's are identical, you could set up one of them to your liking, the use partimage to copy your setup to the others.

---

### Post by entengkabisote on 2005-09-12
i also have question since im going to use ubuntu for the first time for my internet cafe. 

what internet cafe timer manager can i use with ubuntu?

what kind of installation do i need to run windows applications like games:

 - counterstrike
 - ragnarok with gameguard
 - mu online
 - rose online
 - gunbound
 - gunz online
 - pristontale
 - warcraft frozen throne

Thank you so much for your immediate reply.

---

### Post by f1dave on 2005-09-12
wine (free) and cedega (not free) can be used to run windows games. For instance, I run diablo 2 and half life here. However, I do not know if all the games you've listed will be supported. Best to look at the documentation for both.

---

### Post by daller on 2005-09-12
The easiest way to share debs between several computers - is the raw way - IMHO...

Simply access /var/cache/apt/archives/ on the "main" computer, and copy it to the local "/var/cache/apt/archives/"

---

### Post by jeffreyvergara.NET on 2005-09-21
[QUOTE=entengkabisote]i also have question since im going to use ubuntu for the first time for my internet cafe. 

what internet cafe timer manager can i use with ubuntu?

what kind of installation do i need to run windows applications like games:

 - counterstrike
 - ragnarok with gameguard
 - mu online
 - rose online
 - gunbound
 - gunz online
 - pristontale
 - warcraft frozen throne

Thank you so much for your immediate reply.[/QUOTE]

I installed and played CS, WarCraft TFT using CEDEGA, and I guess you can also do it with WINE. 

I tried to install MU Online, but there's an error, but I think it's possible to play it, [READ HERE]](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=282231)
I installed GunZ Online, but not able to Patch so I can't play the game, I also tried it in Ragnarok I guess it'll work, I just don't have the time to patch it, my installer was last 2003 edition.. eheehe... 

I tried Gunbound but no luck...

and other games... I still dont know yet

---

### Post by quebecostarica on 2005-10-14
Hi!

To the moderator:

Please feel free to edit, move or snip or even delete this post! My intention is not to " plug " my site but rather, to " add a value to the Internet " like it is said!

I don't know how I stumbled on this thread about UBUNTO and the word ' cybercafe " but maybe I can be of some help here!

I have a site dedicated about one thing: [I]The world of CyberCafes
[/I]
So if some of your users would like to find anything about Linux and CyberCafe, it's the place to go. It's so hard to find anything related to the Linux operating system (whatever flavor of Linux) related to help manage CyberCafes that I created a category just for that
.
Just  type " Linux " and you will find whatever Linux programs are available to manage cybercafes.

I also included a link to this forum thread...if OK with you. ( just type Linux in the search box ).

Again, and I am sorry to repeat myself, information related to cybercafe linux management software is so rare to find, that I had to add this forum thread.

To Rodrigo:

I hope you will find something that will be useful to your cybercafe.

Roger Pilon, Editor
[ CyberCafe World Wide Resources Directory]("http://www.yourcybercafe.info")

NOTE: if you like the color-style-design of this forum, just click on *Select Style Box* on the left: choose " Image Style ". You will feel a little bit more at home!

---

### Post by seyon on 2005-11-09
Hi,
I have a cybercafé powered by ubuntu :D
i'm using openkiosk to manage it ( [http://openkiosk.sf.net](http://openkiosk.sf.net) )
An i do use cedega from transgaming ( [www.transgaming.com](www.transgaming.com) ) to run windows games like counter-strike 
and the easiest way to share debs between several computers is by using a smb share in the main coputer, and symlinking a share to /var/cache/apt/archives
:KS

---

