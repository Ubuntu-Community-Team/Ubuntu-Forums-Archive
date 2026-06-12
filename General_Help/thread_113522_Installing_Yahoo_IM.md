---
title: "Installing Yahoo IM"
date: 2006-01-06
forum: General Help
---

### Post by Redeyes_Gambit on 2006-01-06
}{ello all!

I'm in a bit of a pickle. I'm trying to install Yahoo Instant Messanger (for unix)  on Ubuntu 5.10 and I run into a bit of trouble. I have done this before on another machine but on this one I didn't complete setup before closing it (I got to the part where it asks for your yahoo ID and password and I had to close it because I didn't know the pass). 

I figured that it was ok since it had a cancell button and all that. well, thing is I came back later to launch yahoo IM and complete the setup and it wouldnt open. It just sat there after I double clicked the icon. So I uninstalled it via synaptec and then tried re-installing it. I went to terminal, typed "sudo dpkg -i yme..." and it asks for password, I give it and it completes. I then go to usr/bin to double-click the ymessenger.sh... and nothing happens. what it should do is launch the setup program... But it doesnt.

I could really use your help 'cause I'm setting this up for a good friend of mine who is going back to college monday and I would love to have it set up for him before then.

---

### Post by FizDev on 2006-01-06
You could instead use Gaim. I believe in comes with Ubuntu 5.10... Or do you really want Yahoo IM?

---

### Post by Redeyes_Gambit on 2006-01-06
Yea, I was realy hoping to have the official yahoo IM program (lol don't ask why :P .) Any ideas?

---

### Post by FizDev on 2006-01-06
In that case I suggest you follow these directions :
[http://ubuntuforums.org/showthread.php?t=81895](http://ubuntuforums.org/showthread.php?t=81895)

> I then go to usr/bin to double-click the ymessenger.sh... and nothing happens. what it should do is launch the setup program... But it doesnt.

For this, I think you should execute it from the terminal. Go to the location where your file is then type
./ymessenger.sh
I think it should start it.

---

### Post by AgonxOC on 2006-01-06
[QUOTE=FizDev]You could instead use Gaim. I believe in comes with Ubuntu 5.10... Or do you really want Yahoo IM?[/QUOTE]

Do you know how to get Gain to work with Yahoo, mine doesnt want to work with it...

Alex

---

### Post by swhit on 2006-01-06
You may need to change your "Pager Port" setting to 20. It's under "Show more options", then "Yahoo Options". I've had to do this in the past to get a connection.

---

### Post by AgonxOC on 2006-01-06
[QUOTE=swhit]You may need to change your "Pager Port" setting to 20. It's under "Show more options", then "Yahoo Options". I've had to do this in the past to get a connection.[/QUOTE]

That didnt remotelly work....    Ohhh I also tried MSN and it doesnt work, the only one that works in AIM...

Alex

---

### Post by Redeyes_Gambit on 2006-01-07
Well I executed it by double clicking before. And the instructions on the site for installing yahoo instant messenger say to double click ymessenger.sh but hey I'll give your way a go....

Ok, terminal gives me the error "segmentation fault" when executing the command you gave me when in /usr/bin. What now?

---

### Post by Redeyes_Gambit on 2006-01-07
*bump* Anybody? I only have one more day

---

### Post by s_spiff on 2006-01-08
There is a package in Syaptic which installs the 'original' yahoo messenger? Or am I supposed to download it from somewhere [ eg: yahoo messenger site? ] if so, how to install it? 
I know this doesn't exactly solver your problems, but I would like use yahoo messnger, and I hate GAIM!

---

### Post by Sef on 2006-01-08
You will have to download Yahoo! IM from yahoo.com.  [http://messenger.yahoo.com/]("http://messenger.yahoo.com/")

It should be simple to set up.  If you continue to have any problems, post it here.

---

### Post by s_spiff on 2006-01-08
thanks, did it, without much problems. But everytime I had to go to the /usr/bin folder to get yahoo on, and so I did a cpy/paste on the desktop. Now I wanted to know , how to change the icon? its presently a 'terminal' type icon, as in desplays a terminal. Hope I'm conveying what I mean to.

---

