---
title: "Avast antivirus for linux"
date: 2006-03-16
forum: Desktop Environments
---

### Post by fairdoes on 2006-03-16
Avast have released a version fo their antivirus program for linux. One download is a tar file, so is intended for us!

I've tried it today and it works. It runs from the folder that the download extracts to, so there is no need to **install** as such. The update facility is from a dropdown menu - top left of the prog.

To run it, i clicked on bin, then avastgui.

It gives the option 'run in terminal?' and this worked (it takes a while to start). These error mesages were displayed, and no doubt they will be simple to older Ubuntu hands then mine ...



P.S. I've tried to help someone with a comment on another thread but don't yet know how to link them. Feel free to put me right!

---

### Post by IGNIZ on 2006-03-16
downloading :rolleyes:

---

### Post by erniewinner on 2006-03-20
wow! thats the first anti virus thats worked for me. i've also downloaded the pc version. nice and simple. looks good too. thanks for the info. :KS

---

### Post by traveller on 2006-03-20
[QUOTE=erniewinner]wow! thats the first anti virus thats worked for me. i've also downloaded the pc version. nice and simple. looks good too. thanks for the info. :KS[/QUOTE]

I agree...

---

### Post by traveller on 2006-03-20
[QUOTE=fairdoes]Avast have released a version fo their antivirus program for linux. One download is a tar file, so is intended for us!

I've tried it today and it works. It runs from the folder that the download extracts to, so there is no need to **install** as such. The update facility is from a dropdown menu - top left of the prog.

To run it, i clicked on bin, then avastgui.

It gives the option 'run in terminal?' and this worked (it takes a while to start). These error mesages were displayed, and no doubt they will be simple to older Ubuntu hands then mine ...



P.S. I've tried to help someone with a comment on another thread but don't yet know how to link them. Feel free to put me right![/QUOTE]

Downloading updates... Thank you!!!

---

### Post by fairdoes on 2006-03-22
It does seem promising! I've tried to add it to the desktop - the icon has appeared in Applications/Accessories, but says [b]Cannot launch entry

 Details: Failed to execute child process "avastgui" (No such file or directory)[/b].

Maybe I didn't set it up correctly? I just added **sudo ** on the front of the instructions given in their install instructions, like this:-

**sudo ./lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh install**.

This ran without error messages, (error messages were shown without the sudo).

I'm sure it's a small problem. :)

---

### Post by az on 2006-03-22
It is proprietary.  It is binary-only.  IMHO you subject your box to far greater risk by installing things from sources such as this instead of using the repositories.



"To protect your home computer running Linux, download avast! Linux Home Edition from this page now"

Protect from what?

---

### Post by mchatel on 2006-03-22
Nice.  Thanks for letting us know.  I'm going to take a look at it.
I used Avast when I ran Windows, and it wasn't bad.

---

### Post by jimcooncat on 2006-03-22
Exactly what is this software supposed to accomplish? Do you think it will help you avoid all those nasty Linux viruses? Please!

I'm running ClamAV for incoming email that will go to Windows client. Why go with anything unsupported when you have this?

---

### Post by fairdoes on 2006-03-22
Thanks for the feedback.

I've searched for clamav in 'add applications' and it's never heard of it. Where do I find it please?

---

### Post by Ramses de Norre on 2006-03-22
apt-cache search clamav will show the correct package name.

---

### Post by MichaelZ on 2006-03-22
Hello,

Ubuntu has the Aegis Virus Scanner :). I have installed it, but never used. I also do not find how to call it :???:.

Best wishes,
Michael

---

### Post by gazj on 2006-03-28
[QUOTE=azz]It is proprietary.  It is binary-only.  IMHO you subject your box to far greater risk by installing things from sources such as this instead of using the repositories.



"To protect your home computer running Linux, download avast! Linux Home Edition from this page now"

Protect from what?[/QUOTE]

I totally understand where your coming from, but my home folder is shared with my girlfriends windows laptop, and avast did pick up a virus in there, i know this probably came from her lappy, and i know its not going to effect my linux box, but hopefully its stopped it spreading to her local drives, although her avast should have picked it up, anyway i don't think its entirely useless, if you share drives with windows machines or dual boot

---

### Post by mrpixels0 on 2006-03-28
Acutally, I would think that as more people migrate to linux from windows this kind of program would become needed. 

Due to the fact that some companies that produce spyware and malware would target it as well as windows, also aren't most Virus's for windows machines written on Linux Based computers ?.

and then there is the Virus that has recently appeared for the Macintosh OS X, I see the Linspire users as major targets of Virus's targeted at linux due to it's ease of use and the fact that the user has root priviliges right off the bat. 
Then add to that fact that not all Linux users are going to becareful setting up thier boxs correctly and will have problems.

seems like the days of the No Virus OS are comming to a close as socitey becomes more and more tech savvy, i hope i am wrong about this assumption but history shows otherwise.

just my two cents.

MP0

---

### Post by Papa-san on 2006-04-01
Just open a terminal and enter:
```
 sudo apt-get install clamav

```

Should do ya just fine!

---

### Post by fairdoes on 2006-04-07
Avast was good on Windows - I'm just pleased they even try to do things for Linux.

MrPixels - **Acutally, I would think that as more people migrate to linux from windows this kind of program would become needed. **
You're telling me - and I hope AdAware join in too.

---

### Post by | MM | on 2006-04-12
I think this is a good thing ... there is obviously going be people who target Linux as it becomes more popular.

avast! is top notch on Windows ... no reason why it shouldn't be on Linux.

Plus i think it will reassure 'enterprise users' that Linux is being taken seriously by proprietary software vendors.  Even if it is somewhat of a placebo in real terms.

---

### Post by spartan777 on 2006-04-21
sorry mm, but linux will remain secure, even as it gains popularity, even if it becomes a mainstream desktop os. that's because linux is BUILT secure. look at apache, another open-source project. something like 80% of all internet servers use it, and yet its as secure as, well, just about anything can possibly be. linux is the same. EVEN if linux viruses started to spread, AND they became harmful (current ones really aren't), all you have to do is stick to the repo's like someone else said, and you'll be safe as can be.

---

### Post by airtonix on 2006-04-22
so, your line of thinking goes like this:

windows is only a security risk becuase lots of people use it, not becuase of the way it cultures a careless user philopshy, no no no laziness is the path to a secure fortress son.

and linux is only free of viri due to its obscurity......not becuase it forces the user to change their way of thinking in regards to their digitial behaviour?

I want to point out that my driving instructor came up with a most excellent idea to make people PAY ATTENTION on the road, it was a spike mounted in the middle of the steering wheel pointing at your head, hot diggidy, you be damned if you weren;t paying attention to your actions!!! lol.

imagine how many cars would be sold if that went ahead. bit like linux really isn't the cultural anti-thesis of mass-tv, "You mean i have to THINK!!! sheesh i'd rather be lead around by the nose being presented with things that Im expected to purchase with money generated from nothing to pay for services that don;t really exist so a bunch of enterprising bankers can sit on a pile of gold and toss themselves into glory." yeah....system of a down's latest album speak volumes about this attitude of compliance...

---

### Post by airtonix on 2006-04-22
and just remember that your ability as a human to overcome and perpetuate your species through adversity is because of adaptability.....not tradition.

---

### Post by airtonix on 2006-04-22
but let me, you know. If i where to be in the unfortunate circumstance where i was forced use a windows machine like so much bad disney...then i would definitly run: avast, sygate firewall, and XP antispy to kill the dlls that talk to M$.

but thats only if i cant first jump out of a window and scream down the road, declaring profane statements about windows and the state of the world. hehehe

---

### Post by crispy_420 on 2006-04-22
Interesting article in linux based malware [here]("http://www.computerworld.com/softwaretopics/os/linux/story/0,10801,110710,00.html").

---

### Post by philetus on 2006-04-23
fairdoes said:

"Avast was good on Windows - I'm just pleased they even try to do things for Linux."

I agree.

---

### Post by tedrogers on 2006-11-04
I just installed it on Edgy and I get this error when running avastgui from console:

test: 95: ==: unexpected operator
(process:6178): Gdk-WARNING **: locale not supported by Xlib
(process:6178): Gdk-WARNING **: can not set locale modifiers

It seems to work okay, but don't know what these mean or if they are affecting how it works?

Plus, how can I stop it...it's annoying. I like a life without error messages, although I know why they exist and couldn't do without them really.

Any ideas anyone?

---

### Post by traveller on 2006-11-04
[> **tedrogers said:**
> I just installed it on Edgy and I get this error when running avastgui from console:
"Installed"? I think perhaps you should try again following the instructions given by fairdoes at the beginning of this thread. 
Here's what I did some mins ago and worked fine for me: double-clicked on the (extracted) folder of avast, then on bin, avastgui and finally clicked run (not in terminal). Updated its database and made a quick scan.
I like avast! has a gui and it's easy to use. I use it without any problems to date.

---

### Post by LTBP5WD2 on 2006-11-04
I had Avast installed but it would not work.  I uninstalled from the Synaptic magager but the  icon that appeared in Applications/Accessories is still there.  How do I get rid of it?

I received the follow script when  I tried to run it so I unistalled it.

06:04:46 PM: can't open file '/home/ltb/.avast/avastrc' (error 13: Permission denied)
06:04:46 PM: can't open user configuration file '/home/ltb/.avast/avastrc'.
06:04:46 PM: Failed to inspect the lock file '/home/ltb/.avast/lockfile-ltb' (error 2: No such file or directory)
06:04:46 PM: Unable to detect whether another instance of avast! is running.
Any sugestions??

---

### Post by tedrogers on 2006-11-05
> **LTBP5WD2 said:**
> I had Avast installed but it would not work.  I uninstalled from the Synaptic magager but the  icon that appeared in Applications/Accessories is still there.  How do I get rid of it?

I received the follow script when  I tried to run it so I unistalled it.

06:04:46 PM: can't open file '/home/ltb/.avast/avastrc' (error 13: Permission denied)
06:04:46 PM: can't open user configuration file '/home/ltb/.avast/avastrc'.
06:04:46 PM: Failed to inspect the lock file '/home/ltb/.avast/lockfile-ltb' (error 2: No such file or directory)
06:04:46 PM: Unable to detect whether another instance of avast! is running.
Any sugestions??

This sounds like some kind of permissions/super user thing...don't know why this would happen though.

---

### Post by tedrogers on 2006-11-05
> **traveller said:**
> [
"Installed"? I think perhaps you should try again following the instructions given by fairdoes at the beginning of this thread. 
Here's what I did some mins ago and worked fine for me: double-clicked on the (extracted) folder of avast, then on bin, avastgui and finally clicked run (not in terminal). Updated its database and made a quick scan.
I like avast! has a gui and it's easy to use. I use it without any problems to date.

Yes...sorry...."installed" is such a MS thing to say. I understand it runs from a self-contained package/folder.

The only difference for me is that I downloaded the .deb (debian) package from the AVAST website added this package using the package manager app in ubuntu.

---

