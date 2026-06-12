---
title: "ies4linux issue...what did I do wrong?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by PapaWiskas on 2006-01-15
I followed everything to the letter.....I think.....but for some reason I get an error when it starts....

anyone know why?
=================  IEs 4 Linux =================
Install IE6, IE5.5 and IE5 on Linux via Wine.
Credits: Sergio Lopes <slopes at gmail dot com>
Project page: [http://tatanka.com.br/ies4linux](http://tatanka.com.br/ies4linux)
See README file for more info

Installation options:
[1] Install IE6, IE5.5 and IE5
[2] Install only IE6
[3] Install only IE5.5
[4] Install only IE5.0
Please choose an option: 1

Downloading everything we need ...
lib/download.sh: line 80: `download-dyn': not a valid identifier

---

### Post by Mr_Grieves on 2006-01-15
I failed to find any informaton about this issue. So I guess I'll just ask..

Whyyyyyyyyyyyyyyyy? :D

Firefox is you friend.. IE does nothing that Firefox can't do..
When someone used IE in Linux God kills a kitten :(

IE4Linux says:

> 
**-The install process fails**

IEs4Linux was tested sucessfully on:

    * Wine 0.9.5 - Ubuntu Breezy, Fedora 3 and 4, Debian, Gentoo, PLD 1.99, Slackware 10.2, Suse 10
    * Wine 0.9, 0.9.1, 0.9.2 and 0.9.3 Note: Wine 0.9.4 has some problems with IEs4Linux. Please try 0.9.5

Wine is a mystery and IEs4Linux may work or not on your Wine. IEs4Linux was tested by friends with the above Wine versions. But it&#8217;s possible (and probable) that it works under other Wine versions.

If you tested ies4linux successfully using another Wine version, please let me know. Contact me at and tell me your Wine version and your Linux distro.


Might be a stupid question, but, do you got Wine 0.9.5?

---

### Post by aysiu on 2006-01-15
[QUOTE=Mr_Grieves]I failed to find any informaton about this issue. So I guess I'll just ask..

Whyyyyyyyyyyyyyyyy? :D

Firefox is you friend.. IE does nothing that Firefox can't do..
When someone used IE in Linux God kills a kitten :([/QUOTE] That's not fair. Rare though they are, there are some sites that work with *only* Internet Explorer (not even User Agent Switcher makes a difference), and if those sites are part of your regular browsing experience, it's not a bad thing to have IE.

Also, if you're a web designer, you need to know how your site is going to look to 85% of the viewing public.

---

### Post by PapaWiskas on 2006-01-15
Yes I have the correct version of wine....I am pretty anal about following things to a "T", and dont like to ask if I dont have to.  But I searched the forums and couldnt find this issue.

I am a website designer, and one of my financial sites I go to requires IE.....

I do not want to go back to Windoze....

And no harm in asking those questions....I use Firefox religiously.....but the agent switcher does not always work.  And I have to check my designs in both browers as well as Opera....

---

### Post by PapaWiskas on 2006-01-15
[QUOTE=Mr_Grieves]
When someone used IE in Linux God kills a kitten :(
[/quote]
Darn it....I love cats...

---

### Post by aysiu on 2006-01-15
It's entirely possible that there's something wrong with the file the script is trying to download and install. That is, the script your running may be doing its job, but the file it's trying to use (which I think is just on a server somewhere on the internet) may have somehow become corrupted... say, around line 80...?

---

### Post by PapaWiskas on 2006-01-15
line 80 is at the end of this snippett
i cant figure out the problem

download-dyn() {
	_getInfo $1
	if [ ! -e "$DOWNLOADDIR/$FILENAME" ]; then tmp=1; fi
	if [ "$FSIZE" = "" ]; then tmp=1; fi
	if [ "$tmp" = "1" ]; then
		wget $FURL $WGETFLAGS --continue -O "$DOWNLOADDIR/$FILENAME"
		md5=`$MD5SUM "$DOWNLOADDIR/$FILENAME"`
		size=` du -sk "$DOWNLOADDIR/$FILENAME" | awk '{print $1}' `
		echo export MD5_${1}=${md5:0:32} >> ~/.ies4linux/config
		echo export SIZE_${1}=$size >> ~/.ies4linux/config
	else
		download $1
	fi
}

---

### Post by PapaWiskas on 2006-01-16
still banging my head against the wall on this issue.

I have tried to even change permissions on my directories where all of this was extracted to, but not even that fixed it.
Does anyone know if this particular script still works?

Is there another method similar method to this one to get IE installed....

---

### Post by aysiu on 2006-01-16
You may want to contact the developer about it.

After all, when [a Google search for your error](http://www.google.com/search?hl=en&q=lib%2Fdownload.sh%3A+line+80%3A+%60download-dyn%27%3A+not+a+valid+identifier&btnG=Google+Search) turns up nothing, that means it may be some new problem worth addressing.

The dev's contact info is [here](http://www.tatanka.com.br/ies4linux/en/faq/#where).

---

### Post by aysiu on 2006-01-16
Maybe something's wrong with 5.5 or 5?
I just ran IEs4Linux and did only 6 and didn't have any problems.

**Edit**: Scratch that. It worked for the others as well. Maybe the server was down at the time you were running it. Try running it again now.

---

### Post by PapaWiskas on 2006-01-17
im not sure what the problem is....I still can not run it.

I ended up using the "sidenet" method and that got it installed for me finally.

Thanks for all your help.  :D

---

### Post by Nandro2 on 2006-02-15
I just installed it myself, and it didnt seem like it was working, turns out I needed to sudo run it in order for it to work from the CL as just clicking on it and hitting run wouldnt do it.

---

