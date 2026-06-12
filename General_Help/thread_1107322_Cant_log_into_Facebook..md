---
title: "Cant log into Facebook."
date: 2009-03-26
forum: General Help
---

### Post by crq91 on 2009-03-26
Hello, MY hard drive is split right. it is between ubuntu and windows and i can log onto facebook from windows and from my itouch but whenever i try to log on form ubuntu it goes to the first login page but after i type in my password and email it just loads forever. and i know its not facebook because i can log on from windows and stuff. any ideas

---

### Post by LowSky on 2009-03-26
facebook should work, but then again have you installed java, that could be the issue

simple enough to fix, and this will solve some other questions you might have later, like Flash, MP3 and other codec issues

go to a terminal (Top panel, Applicaitons>Accessories> Terminal

type 

```
sudo apt-get install ubuntu-restricted-extras
```

follow the prompts (note hitting TAB will move the cursor to yeas at the java question page)

restart and all should work well

---

### Post by crq91 on 2009-03-26
why thank you my good sir. your help is much appreciated

---

### Post by crq91 on 2009-03-26
nevermind it still doesnt work...i tryed what you suggested but it still wont login. any ideas

---

### Post by KCG102282 on 2009-03-26
It works on my end.

---

### Post by crq91 on 2009-03-26
yeah see thats why i think that its something with my computer....because my internet works and facebook works on windows

---

### Post by rmausser on 2009-04-17
I can confirm I am having this problem as well on jaunty

---

### Post by meeko on 2009-04-17
Maybe the problem is firefox specific? First I'd try making sure Firefox is set up properly to handle cookies, etc. If that doesn't work, try installing another browser that uses a different renderer. Something like opera might work better.

---

### Post by ericd8027 on 2009-04-25
I have recently installed Jaunty Jack and Dan's Guardian and have been prohibited from accessing Facebook as well.  

It becomes listed as Weighted Phrase Limit Exceeded

How do I as a recent n00b to Ubuntu update the exception list?:confused:

Any and all help appreciated!

Eric

---

### Post by sports fan Matt on 2009-04-25
Facebook works here as well...not sure why its not on your guys end:(

---

### Post by ericd8027 on 2009-04-26
So this problem extends to downloading mp3s as well.  Also, when I go into the exceptions list and add facebook ([http://www.facebook.com/](http://www.facebook.com/)) and save, nothing changes.  It is still filtered out.  Do I need to put something more than just the URL?  Is there a walk-through on how to edit the exceptions lists?

---

### Post by ericd8027 on 2009-04-27
Problem resolved.

---

### Post by timjohn7 on 2009-06-03
> **ericd8027 said:**
> Problem resolved.
How?  I have the same facebook issue using Opera 10 Beta.  Your solution may help... also please mark the thread as solved so that others may benefit from your experience.

---

### Post by trench.me on 2009-06-03
Facebook not loading is a fix, not a bug.

:)

But I digress... (sigh), I'd highly recommend trying out a new version of your current browser before jumping-ship on your browser. If you are on Firefox, don't run away because you can't see who's poked you today - try upgrading to the newest beta, see if that helps.

[http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

If it doesn't, then speak up. We need to find out what's causing this even though it's related to a site I despise. 

(I don't digress well, apparently.)

---

### Post by Pyorrhea on 2009-06-11
I am having this same issue. I spent some time searching this forum for answers as well as googling my way through the internets.
 
I think this has something to do with java not being installed.
 
What I have done :
 
Downloaded jre-6u13-i586.bin from java website.
 
Opened terminal.
 
File is executeable checked with the [file /path/filename] command.
 
I then gave it rights to execute from the saved location with [chmod +x filename].
 
Then executed the file with [sudo install ~/Desktop/downloads/filename]
 
I was prompted to agree to the TnC's, accpeted it and it completed.
 
Tried facebook, and still it does not load. Check in the browser if the plugin was installed with [about:plugins], there was no plugin for java. I also restarted and there was still no plugin.
 
Opened terminal and used [java -version] and it tells me that it is not installed.
 
Then went to the folder where the .bin extracted to or installed to, not sure if it installed or just extracted.
 
And ran the following cmd, [sudo install ~/Desktop/downloads/java/java6_runtime] the file is there as it auto completes when hitting tab. I might not have set chmod +x for this file, but the error message that I get states that it cannot find the file.
 
Halp! 1st time user and I am kinda stumped.
 
Thanks for your help in advance.
 
Pyo :)

---

### Post by matborda on 2009-06-19
I have this problem, too.

as Crq91 said, Facebook can be accesible with windows but not with ubuntu.

in ubuntu i tried firefox, epiphany and opera, but i still can't login into facebook.

sometimes i can log in, but i can't do nothing (go to my friend's profiles, write a comment, etc...). curiously, i can see the videos posted in the Home page.

Thanks for the attention

Mattia

---

### Post by running_rabbit07 on 2009-06-19
"Facebook not loading is a fix, not a bug."

Funny!

Sounds to me like the needed add-ons aren't there. Not that I want to but I can sign into my facebook without problems. When I first reloaded Ubuntu onto this PC I made it my mission to not have to load Windows even to do my college classes. In order to do that I had to get all the add-ons so that I could view the lectures and slide shows on line. I am getting close to forgetting what my Windows desktop looked like.

And of coarse after ericd8027 figured out his own fix, he is not going to share it.

I can say I found most of the add-ons were in the add/remove and/or synaptic package manager. I installed 2 or 3 things from there that had Lava in the description and they worked.

---

### Post by itix on 2009-06-19
Facebook works for me. I think there might be some sort of connection error with Linux Firefox or something. I cannot accurately describe it though. Try again later...

---

### Post by matborda on 2009-06-19
solved with

```
sudo ifconfig eth1 mtu 1360

```

where **eth1** is my wireless connection.

---

### Post by countryjake on 2009-06-19
are you all using firefox? try a different browser, maybe opera or epiphany? there are a bunch of them in applications > add/remove programs
Just select the internet category on the left and set it to All Available Applications.

If that works, then it must be a problem with the install for firefox on your computer, go back to add/remove programs, uncheck firefox and apply, then check it again to reinstall. Hopefully it should work then.

If this does not work, then i have no idea.

---

