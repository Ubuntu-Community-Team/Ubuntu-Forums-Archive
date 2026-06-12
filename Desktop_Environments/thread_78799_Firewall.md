---
title: "Firewall"
date: 2005-10-18
forum: Desktop Environments
---

### Post by microo on 2005-10-18
Hello !

Since we have a problem on our hands getting Firestarter functionning like it was on Hoary. 

What kind of firewall could you suggest to replace it ?

Or any clear suggestion on how to fix Firestarter are welcome (Firestarter is not a bad firewall when it works well )

Waiting for advice gentlemen

Thank you: -\"

---

### Post by Dr. Nick on 2005-10-18
What problems are you having with firestarter, Its not actually a firewall itself, just a front-end to configuring iptables which is the actual firewall. Are you just trying to get it to run on startup or something?

*Off topic*
Nice avatar :)

---

### Post by neutro on 2005-10-18
I personnally use shorewall, which is another front-end (but not graphical) to iptables. If you're ready to read a quick startup guide, it works well, but it's rather far from firestarter in terms of usability. It's probably much more flexible, though.

---

### Post by scottl on 2005-10-19
Hello,

What problems are you having? I'm fairly new with Linux/Ubuntu but have been running Breezy Badger with Firestarter for about one month without an issues.

Scott

---

### Post by Goober on 2005-10-19
Not to discourage anybody, but if all you are doing on the net with Ubuntu is browsing and E-mails, you don't need a Firewall.  Of course, it makes people feel more secure, since we are all so used to having one with Windows, but for Ubuntu, its not really necessary.  You might wanna have one if you are downloading pirated stuff, just *in case* . . .

---

### Post by anil_robo on 2005-10-19
I'm running Ubuntu breezy for the last six days, and firestarter for the last three days. I do not browse any illegal sites or download any pirated stuff. Still, I notice that firestarter blocks some connections, and informs me by change of its tray color icon. Since I hardly have any technical knowledge of networks, I do not know :
1. What does it mean?
2. What should I do about it?
3. Am I secure?

---

### Post by angkor on 2005-10-19
[QUOTE=anil_robo]
3. Am I secure?[/QUOTE]

Go to [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
 
and see if you've got any ports open. Ubuntu ships with all ports closed as far as I know, so you're very safe and secure.

---

### Post by bam on 2005-10-19
how do you get it to run at startup?

---

### Post by anil_robo on 2005-10-19
[quote=bam]how do you get it to run at startup?[/quote]

From the main menu:

1. System --> preferences --> sessions
2. Go to last tab (startup programs)
3. click "add"
4. in the new dialog box that pops up, type "gksudo firestarter"
5. Close, and restart your system.
6. FIrestarter will now start with your system, and it'll ask for a password everytime.
Note: When I enter the password before my network is properly configured, I get an error message. So, usually I wait for 1 minute after startup and then enter the firestarter password.

After you've started firestarter, check this website: [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")
(Many thanks to Angkor for the link :D)

---

### Post by microo on 2005-10-19
I always have to write down my password and that even if i write in the sudoers part (my username ALL=NOPASSWD: /usr/sbin/firestarter at the end of the file )

Do i have to put this sign # before to make it work ?

Why can't we see the events number ?

Need help for this one 

Thanks   

Do i have to get rid of that line below #members of the admin group may gain root privileges
                                                            % admin ALL=(ALL) ALL 

or change it with my username ALL=NOPASSWD: /usr/sbin/firestarter

---

### Post by akiro.yamamoto on 2005-11-29
microo:
I just got this info:
CODE: 
sudo visudo
username ALL=NOPASSWD: /etc/firestarter

---

