---
title: "mozilla $url - amsn"
date: 2007-11-19
forum: Gaming &amp; Leisure
---

### Post by mattmill30 on 2007-11-19
Hey,

I've been having a lot of trouble with amsn.
Anything that linked outside of the program, such as running/viewing a received file, or loading my emails, would popup an error such as
[B]Emails: mozilla $url
File Manager: my_filemanager open $location[/B]

After a few days of looking into it, I've realized that its quite a simple problem, I don't have mozilla, I have mozilla firefox. Therefore, amsn was correct, it couldn't load mozilla, because the filename for mozilla firefox is firefox.
**If you replace 'mozilla $url' with 'firefox $url', your email will load.**
Any browser can replace mozilla, but I have used firefox as the example because it is the default web browser for ubuntu.

Swiftweasel:
If you are using swiftweasel from automatix, you must include the address to the browser, not just the name.
So 'mozilla $url', will be replaced with '/opt/automatix/swiftweasel/swiftweasel $url'.

I hope this has been of use, when I manage to find out what the command/program is to load the file manager, i'll add it.

---

### Post by Vesper007 on 2008-02-12
Thank you!!  I have been using aMSN for several weeks and you have fixed my error....of course! I have firefox as well and it never occurred to me to go to preferences and change. I was assuming that mozilla and firefox are the same. I guess they are not. 

way to go* mattmill30*...aMSN seems to be working as it was intended and for the first time since i've been using it. :)

---

### Post by Licurgo on 2008-02-16
mattmill30:
Thanks a lot, I've been a few hours looking here and there and I couldn't resolve the problem.
But with this tutorial in seconds was working all right
Thanks
:lolflag:

---

### Post by Lenc on 2008-03-05
I have the same problem... could you tell me where can I find this text to replace it?

thank you!

---

### Post by giannis1_86 on 2008-03-06
Thank you very very much..It work for me too...

---

### Post by robelliott2125 on 2008-04-08
> **mattmill30 said:**
> Hey,
After a few days of looking into it, I've realized that its quite a simple problem, I don't have mozilla, I have mozilla firefox. Therefore, amsn was correct, it couldn't load mozilla, because the filename for mozilla firefox is firefox.
**If you replace 'mozilla $url' with 'firefox $url', your email will load.**
Any browser can replace mozilla, but I have used firefox as the example because it is the default web browser for ubuntu.

Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you!!!

I originally installed aMSN when i started using ubuntu, but gave up on it because of the basic errors, since reinstalling, i thought i'd have a proper bash at everything second time around, and you've just helped me sort out one of the first probs i had.

Thank you!

---

### Post by doorknob60 on 2008-04-08
This is in the wrong forumm, it needs to get moved. I already knew this, but it took me a while to find it, and I would have liked to see this when I was new to Ubuntu :P

---

### Post by Karthik_nk on 2008-04-23
Thank you...that worked as a treat!!

---

### Post by piricoco on 2008-04-29
Hi,
I've Kubuntu Hardy final and Firefox 2.0.0.14 installed from the binaries (in my home/Programs directory), not from synaptic. This trick didn't work for me: I receive the same message (verify preferences), but I've set up in aMSN "firefox $url".
Maybe I'd have to set up a symbolic link? When I type "firefox" in Konsole it responds me that firefox is not installed (please install with apt-get) and a message from bash: firefox: command not found.

Bye!

---

### Post by Bölvaður on 2008-04-29
to open received files in file manager:
File Manager : nautilus $location

to open the received files:
Open file command : gnome-open $file

---

### Post by piricoco on 2008-04-29
> **Bölvaður said:**
> to open received files in file manager:
File Manager : nautilus $location

to open the received files:
Open file command : gnome-open $file

Is it an answer to my question? I use **K**ubuntu and my problem regards firefox...

---

### Post by Bölvaður on 2008-04-29
> **piricoco said:**
> Is it an answer to my question? I use **K**ubuntu and my problem regards firefox...

uh no sorry I didn't read down all the tread, it was reply to other people that I thought might not know how to do it.

But your problem should be pretty simple to do with Konqueror rather than firefox.

You can test it in Konsole : konqueror [www.bbc.co.uk](www.bbc.co.uk)

So on aMSN you can add:

Browser : konqueror $url
File manager : dolphin $location
Open file command: kfmclient exec $file

you can test the opening files part by open up Konsole and type "kfmclient exec file:/home/your_username/Pictures/your_photo.jpg" (note that this is case sensitive when you insert your user name and name of the photo).

---

### Post by piricoco on 2008-04-29
> **Bölvaður said:**
> uh no sorry I didn't read down all the tread, it was reply to other people that I thought might not know how to do it.

But your problem should be pretty simple to do with Konqueror rather than firefox.

You can test it in Konsole : konqueror [www.bbc.co.uk](www.bbc.co.uk)

So on aMSN you can add:

Browser : konqueror $url
File manager : dolphin $location
Open file command: kfmclient exec $file

you can test the opening files part by open up Konsole and type "kfmclient exec file:/home/your_username/Pictures/your_photo.jpg" (note that this is case sensitive when you insert your user name and name of the photo).

Thanks for your response, Bölvaður, but I some have different preferences, although I LOVE KDE :)
I prefer Firefox for web browsing and Konqueror for file managing: I use Firefox under windows XP since 4 years, and I prefer Konqueror to manage files because of its configurability.
I think that I am (a little) off thread, but I'd like to know how I can set up firefox to be accessible via konsole, in order to open URLs with it form aMSN: I think that's a problem of environment variables, but I'm a newbie in linux and I don't know how to do it. If you can't answer me, Bölvaður, is there anyone that help me?

Greetings ;)

---

### Post by bilal.17 on 2008-04-29
i had the exact same problem and i solved by using the same logic you used a while back ago. It was quite simple after i thought about it.

---

### Post by piricoco on 2008-04-30
> **bilal.17 said:**
> i had the exact same problem and i solved by using the same logic you used a while back ago. It was quite simple after i thought about it.

Can you explain your solution? :confused:

---

### Post by piricoco on 2008-04-30
I added my installation directory of Firefox, i.e. /home/piricoco/Programs/Firefox, in the .bashrc file located in my home folder: now I can start firefox from Konsole, but the problem in aMSN persists, probably because of I'd set some "global variables" to link my firefox to this IM program...

Any idea to do this?!? :confused: [-o<

---

### Post by Bölvaður on 2008-04-30
I'm sorry but I do not know how to do it, I think there are tutorials I saw it being done in... but might be wrong.

In the mean time you can check how you start up Firefox (check commands on the shortcuts and such) then just place that path and file name to your aMSN config.

You can test it out via bash (Konsole/Terminal... what ever) by having the long path at front and then place the URL:

(path/program) (URL)
opera [www.hi.is](www.hi.is)

---

### Post by piricoco on 2008-05-01
Ooops...it was a so stupid thing?
In aMSN I simply set up ~/Programs/Firefox $url and now it works! :)

Thanks, for me the problem is solved, bye!

---

### Post by konstantinos1980 on 2008-07-11
Thanks a lot my man!!!I had the same problem, until I read your solution!!!
So I did it and I have to say that it works perfectly!!!

---

