---
title: "Java + Firefox"
date: 2005-01-29
forum: Desktop Environments
---

### Post by philip41 on 2005-01-29
I am not to sure whether or not this is a firefox or website problem, but when i use the following [SITE](http://linuxsurvival.com/index.php?module=ContentExpress&func=display&ceid=1&meid=-1)  on my Ubuntu box, the java applet seems to be very odd. As in picture 1.

On my windows box with Firefox i get the Applet appearing  correctly as in picture 2.

I have today installed the latest Java Package.



Does anyone no what the problem could be.

---

### Post by philip41 on 2005-01-29
Maybe someone would be kind enough to click on the [Link](http://linuxsurvival.com/index.php?module=ContentExpress&func=display&btitle=CE&mid=&ceid=5)
 to tell me if the Start Module button looks normal or not.

---

### Post by kultuur on 2005-01-29
That button looks normal on my computers.

Tested on ubuntu hoary with sun-j2re1.5.0
and gentoo linux with blackdown-jre-1.4.2

---

### Post by philip41 on 2005-01-30
[QUOTE=kultuur]That button looks normal on my computers.

Tested on ubuntu hoary with sun-j2re1.5.0
and gentoo linux with blackdown-jre-1.4.2[/QUOTE]

I have got Hoary with the sun j2re1.5.0 aswell.

Hmm thats not good then for me, does anyone no what could have gone wrong.
Are there any settings in Firefox that could need altering.

---

### Post by shmonkey on 2005-01-30
Look in /usr/lib/mozilla-firefox/plugins to see if there is a symbolic link to libjavaplugin_oji.so if not then you need to create it.

---

### Post by philip41 on 2005-01-30
Under /usr/lib there are two directories 1) is mozilla-firefox the other is mozilla, they both have a symbolic link to libjavaplugin_oji.so, the one in /usr/lib/mozilla-firefox is 275 KB, the other in /usr/lib/mozilla is 58 bytes.

---

### Post by Viro on 2005-01-30
If it is a symbolic link, where is it pointing to? It should point to your where you installed Java. I don't have Java on my machine so you need to post what it's linking to. There could be an error here and it's linking to the wrong file somewhere.

---

### Post by philip41 on 2005-01-30
[QUOTE=Viro]If it is a symbolic link, where is it pointing to? It should point to your where you installed Java. I don't have Java on my machine so you need to post what it's linking to. There could be an error here and it's linking to the wrong file somewhere.[/QUOTE]

Ok then the link in the /usr/lib/mozilla-firefox is pointing to the correct directory.Also in the home directory there is a .mozilla folder with the same symbolic link, this also is pointing to the above directory.
However in the other /usr/lib/mozilla directory the 58byte link is a broken link.!

---

### Post by philip41 on 2005-01-31
Can anyone give me some advice please. even a hint would do.

---

### Post by ollietc on 2005-01-31
Along the same lines as the problem above, i have installed JRE 1.5 and when my wife goes to [www.uproar.com](www.uproar.com) and plays family feud using firefox, it will start the java app and all appears fine, but text input is delayed so much that you can not play the game. I know, sounds kinda silly, but she is cursing Linux because the only thing she uses my laptop for is to play this game in the living room while watching tv.

---

### Post by philip41 on 2005-01-31
[QUOTE=ollietc]Along the same lines as the problem above, i have installed JRE 1.5 and when my wife goes to [www.uproar.com](www.uproar.com) and plays family feud using firefox, it will start the java app and all appears fine, but text input is delayed so much that you can not play the game. I know, sounds kinda silly, but she is cursing Linux because the only thing she uses my laptop for is to play this game in the living room while watching tv.[/QUOTE]

I can sypathise with you,her on that, i am trying to learn linux and that site above is one of the main sites i like to use for now, but because of this problem i am having to use my windows box  :-( .

Hopefully some nice person with the answer may stumble across this thread.

---

