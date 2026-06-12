---
title: "Getting Netzero to work"
date: 2006-03-06
forum: Desktop Environments
---

### Post by EMCOgre on 2006-03-06
All,

I'm trying to get Netzero to work on Breezy, with little luck.  I've installed the netzero.deb from their website, which creates a bunch of files in the /opt/nzclient folder.  When I try to 'sudo bash runclient.sh' (I believe this is the correct way to start this program) it echoes a line to the screen and then nothing.

I know some of you out there have been able to get this to work, so any suggestions?

Thanks in advance!
Rob

---

### Post by angrykeyboarder on 2006-03-06
[QUOTE=EMCOgre]All,

I'm trying to get Netzero to work on Breezy, with little luck.  I've installed the netzero.deb from their website, which creates a bunch of files in the /opt/nzclient folder.  When I try to 'sudo bash runclient.sh' (I believe this is the correct way to start this program) it echoes a line to the screen and then nothing.

I know some of you out there have been able to get this to work, so any suggestions?[/QUOTE]

Uhh. Get a "real" ISP?

Or Broadband? ;-)

---

### Post by EMCOgre on 2006-03-06
Helpful.  ;) 

When I can, I will.  I'm hoping to get cable BB up and running soon, but I have to wire my house up first.  Crawlspace.  Spiders.  Ick.  In the meantime I deal with what I have.

Thanks,
Rob

---

### Post by djheadley on 2006-03-06
Try this
sudo bash /opt/nzclient/runclient.sh

---

### Post by jason.b.c on 2006-03-06
So i assume you know about Netzero charging extra $$$$$ for long distance?;) , right?
If you have long distance on your phone then thats what you will be connecting with, dosn't seem like such a good deal to me!:(

---

### Post by djheadley on 2006-03-06
What are you talking about?  I've been using Netzero for a couple of years now and don't know anything about this.

---

### Post by jason.b.c on 2006-03-06
> What are you talking about? I've been using Netzero for a couple of years now and don't know anything about this.

Well all i know is when i tried to install it on my computer i couldn't even get connected to finish setting up my account. I soon figured out why, the numbers that its dialing to connect to the internet are long distance;) .( Not 1-800- numbers or of the like )! :p i know i sure couldn't do it!


> years now and don't know 

I saw there commercial on TV recentely and it stated ( some long distance charges may apply in your area )

---

### Post by djheadley on 2006-03-06
Did you check their web site for phone numbers in your area before you sifned up?  I did that first thing.  Yes, I know Netzero is a pain to use in Linux but there are 3 phone numbers in my area that are NOT long distance.  As with any ISP, you need to check out the availability of numbers that are local for you.

---

### Post by EMCOgre on 2006-03-07
[QUOTE=djheadley]Try this
sudo bash /opt/nzclient/runclient.sh[/QUOTE]

I was bashing it from the nzclient directory, so this shouldn't be any different.  I'll try it anyway, though.  My guess is that I'm not launching the Java instructions at the end of that script file.  Would there be some Java packages I need to load?  

Now, does anyone besides djheadley have a comment relevant to my post?  :) 

Thanks,
Rob

---

### Post by djheadley on 2006-03-07
Dumb question, but have you installed java? I was stumped at this point until I realized that I didn't have java installed.

---

### Post by EMCOgre on 2006-03-07
<SMACK!> to forehead.

Ich bin dumbass.

I'll do this, and if I don't have any luck, I'll be back.

Thanks,
Rob

---

### Post by sliverman69 on 2006-03-27
so where did you go to get the java you needed?

---

### Post by mdmarmer on 2006-03-27
It works better if you don't install the .deb and just connect to it.

Instructions from Mepislovers:

[http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=15025&forum=9&post_id=103402#forumpost103402](http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=15025&forum=9&post_id=103402#forumpost103402)

Mike

---

### Post by djheadley on 2006-03-27
here's the instructions from the Sun site:

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

Download the binary file.

---

### Post by sliverman69 on 2006-03-27
thanks, I downloaded it a while ago.  I wasn't sure if I had the right file. Now I know which file it is.
BTW, did you ever fix those two problems you were having when you wanted to run the netzero and gaim?
just curious as to the progress and willing to help in any way possible as soon as I can just get on the blasted net in Ubuntu.  If you ever need someone to help test etc., I will be willing to help out.  Also, do you know what the "DM set to off" means? I am curious and want to know.
Thanks Djheadley

---

### Post by sliverman69 on 2006-03-27
although, after seeing the site that the link sent me to, I may not have the file.  Either way, thanks for the link and the help.

---

### Post by djheadley on 2006-03-27
Gaim works fine but I still have to start Netzero twice unless I have just rebooted.  I think it has something to do with Netzero's updates, but at least it works.  I have used Ubuntu exclusively to get on the net ever since I got it to work.  Thanks.

---

### Post by sliverman69 on 2006-03-27
well, I think that I am going to give it a go again so you may not see me for a while on the forums depending on how well it goes

---

