---
title: "mail to: links not working correctly"
date: 2005-01-21
forum: Desktop Environments
---

### Post by mattack on 2005-01-21
I'm using Firefox 1.0 and Thunderbird 1.0 as my default web browser and mail client respectively with Ubuntu Linux 4.10. I'm somewhat of a Linux n00b so please forgive me...

When I click on a mailto: link in Firefox, one of two things happen, depending on if Thunderbird is open or not.
If T-bird is open I get the "choose user profile" dialogue and cannot proceed with my default (and only) profile beacuse it is in use.
If T-bird is not open, it opens normally with my default profile, but it only checks the mail and not open a window to compose a message. The program will behave normally though, so If I click "create a new message" or hit Ctrl-N, a new message window appears.

I would like T-bird to open a new message window when I click on a mailto: link weather it's already open or not.
Any suggestions?

---

### Post by munk on 2005-01-23
Hi,

Enter the following into Computer / Desktop Preferences / Preferred Applications / Mail Reader / Custom Mail Reader:

mozilla-thunderbird -compose %s

Seems to work fine whether or not Thunderbird is already open or closed

---

### Post by mattack on 2005-01-23
[QUOTE=munk]
Seems to work fine whether or not Thunderbird is already open or closed[/QUOTE]

Not for me...  If Thunderbird is open is still get the "choose a profile" dialog...

---

### Post by munk on 2005-01-23
Hmm, are you sure the 'custom mail reader' option was selected on that tab? Was there anything else in the text field apart from what I suggested? Maybe post a screenshot of how that window looks?

---

### Post by mattack on 2005-01-23
[QUOTE=munk]Hmm, are you sure the 'custom mail reader' option was selected on that tab? Was there anything else in the text field apart from what I suggested? Maybe post a screenshot of how that window looks?[/QUOTE]

absolutely sure. i just double checked to be even more sure. I copy/pasted what you posted to be even more sure than that...   :D 

it still gives me the "choose a profile" dialog if T-bird is already open...  :confused:

---

### Post by dirtpupfc on 2005-02-12
[QUOTE=munk]

mozilla-thunderbird -compose %s

[/QUOTE]

Cool. Thanks. This is the solution that worked for me.

---

### Post by Davepet on 2005-02-12
mattack,

Which version of Ubuntu are you runnung?
If Warty, where did you get your upgrade to v1.0 of firefox? I got mine from the Moilla site& it doesn't seem to integrate well into Ubuntu. There are some simple scripts/tweaks to make it work, though.

Let me know..

Dave

---

### Post by ember on 2005-02-12
It didn't work for me either, yet I have a solution, maybe you'll look here:

[http://www.ubuntuforums.org/showthread.php?t=12887&highlight=Firefox+Thunderbird](http://www.ubuntuforums.org/showthread.php?t=12887&highlight=Firefox+Thunderbird)

I'll have to modifiy that script to raise Thunderbird on a second click on the desktop, but as for mailto-links it works.

---

### Post by mattack on 2005-02-13
I started with Ubuntu 4.10, but might have upgraded... 
Honestly I'm not sure (which is bad, I know). Is there and easy way to tell?
I got Firefox 1.0 from the Ubuntu Backports and it seems to wrok well. It does close at random times however...

The mailto: problem is still there. Any help you have would be great.

---

### Post by Davepet on 2005-02-14
type: "about:config" into the firefox  address bar

Scroll down & see if there is a line reading " network.protocol-handler.app.mailto ", if not,right click on any line & select "new" & then "string"

in "new string value" box type: " network.protocol-handler.app.mailto " click OK

in "enter string value" box enter: " path to thunderbird " & click OK

Just to be clear, " path to thunderbird " means to enter the correct path to the thunderbird shell script for *your* machine.

If the line already exists, just edit it so it points to your T-bird shell script.

Dave

---

### Post by mattack on 2005-02-14
I'm confused about this shell script thing... I don't have one.
should I use the one in the link that ember posted?
and exactly what do I do? Make a file with that in it?
What do I call it? and where should I save it?

---

### Post by Davepet on 2005-02-14
Well, I don't know about Ember's script, but the instructions I posted were all I needed to do. Try those steps first, if you haven't already.


I *did* use a script to get links in Thunderbird to open in Firefox. You create the script in a text editor (like gedit). You can save it just about anywhere, then I went to about:config to point Tbird to the script location when links are clicked.

Dave

---

### Post by mattack on 2005-03-19
Okay, I just figured out how to get mailto: links in Firefox to work correctly regardless if Thunderbird is open or not!

I installed an updated version of the mozex extension available [here](http://www.extensionsmirror.nl/index.php?showtopic=70&hl=mozex) 

Then I followed the instructions [here](http://forums.mozillazine.org/viewtopic.php?p=146623&highlight=mozex#146623) altering some paths in the script as follows:

 ```
#!/bin/sh
#
#script author: asterix
#http://forums.mozillazine.org/viewtopic.php?p=136157#136157
export MOZILLA_FIVE_HOME=/usr/lib/mozilla-thunderbird
if [ $(ps aux | grep thunderbird | wc -l) -gt 4 ]; then
# thunderbird is running (thunderbird est lance)
 $MOZILLA_FIVE_HOME/mozilla-thunderbird-bin -remote "mailto($1?subject=$2)"
else
# thunderbird is not running (thunderbird n'est pas lance)
 $MOZILLA_FIVE_HOME/mozilla-thunderbird-bin -P default -compose mailto:$1?subject=$2;fi
``` 

Now when I click a [EMAIL=test@test.com]mailto:[/EMAIL] link, it works correctly!

P.S. I also got mozex to handle aim/gaim links correctly too!

---

### Post by Davepet on 2005-03-19
Glad you got it working....I guess there's several ways to do it;o)

Dave

---

### Post by ming0 on 2005-03-27
Awesome fix! I've even improved it a little bit, and the user won't need to even install any extensions for it... 

Here it is, step by step:
     
1.) Type: **about:config** into the firefox  address bar
 
2.) Right click and choose: **New>String**

3.) In "new string value" box type: **network.protocol-handler.app.mailto** click OK
 
 4.) In "enter string value" box enter: **/usr/lib/mozilla-thunderbird/thunderbird-mailto.sh** & click OK

5.) Open a terminal and run **sudo gedit /usr/lib/mozilla-thunderbird/thunderbird-mailto.sh**

6.) Copy all of the text inside the box into gedit:```
 #!/bin/sh
#
#script author: asterix
#http://forums.mozillazine.org/viewtopic.php?p=136157#136157
export MOZILLA_FIVE_HOME=/usr/lib/mozilla-thunderbird
if [ $(ps aux | grep thunderbird | wc -l) -gt 4 ]; then
# thunderbird is running (thunderbird est lance)
 $MOZILLA_FIVE_HOME/mozilla-thunderbird-bin -remote "mailto($1?subject=$2)"
else
# thunderbird is not running (thunderbird n'est pas lance)
 $MOZILLA_FIVE_HOME/mozilla-thunderbird-bin -P default -compose mailto:$1?subject=$2;fi 
``` 
7.) Save and exit gedit

8.) In the terminal, enter: **sudo chmod 755 /usr/lib/mozilla-thunderbird/thunderbird-mailto.sh**

9.) Reset Firefox and try the [email="test@test.com"]mailto[/email] link (it should work while TB is on or off)

PM me if there are any errors in this howto (btw, I'm going to put it up in the howto section)

---

### Post by mattack on 2005-03-27
Oh wow, I never thought of putting it in the how-to section. Great idea!
Looks good.

---

### Post by ming0 on 2005-03-27
Oh, did you get my PM about the AIM links? I've been wondering how to use that.

And as for the howto, I can't beleive that this is even an issue! It seems like firefox and thunderbird should work together flawlessly??? Oh well :)

---

### Post by Georges on 2005-04-09
[QUOTE=ming0]Oh, did you get my PM about the AIM links? I've been wondering how to use that.

And as for the howto, I can't beleive that this is even an issue! It seems like firefox and thunderbird should work together flawlessly??? Oh well :)[/QUOTE]

I simply *corrected* the buggy thunderbird startup script and it worked for me
[http://ubuntuforums.org/showthread.php?p=123529#post123529](http://ubuntuforums.org/showthread.php?p=123529#post123529)

Georges

---

