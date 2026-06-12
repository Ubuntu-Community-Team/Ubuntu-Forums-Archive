---
title: "Odd Ubuntu behavior, Corrupted? Virus? First time I've seen this"
date: 2009-05-03
forum: General Help
---

### Post by DesiArnez6 on 2009-05-03
Firefox consistently crashes, when on another browser, I can surf fine, BUT, my firewall is currently blocked to all traffic, so, why am I able to surf the web the the firewall slammed to all?

---

### Post by MaxIBoy on 2009-05-03
Well, you could try downgrading firefox to an older version. Another thing to try is disabling all your Firefox themes/plugins/add-ons, as these can cause instability.

However, if you can surf just fine on another browser (epiphany or opera are both excellent,) why not just go with that?

---

### Post by Paqman on 2009-05-03
> **DesiArnez6 said:**
> my firewall is currently blocked to all traffic

What have you used to do this with? Firestarter? (G)ufw?

---

### Post by DesiArnez6 on 2009-05-03
Yep firestarter, Pressed locked button, I still see traffic? IRC and Web accessible (with other browser)

All of a sudden firefox went half sized and hard crashed, Actually first a firestarted red warning, then Firestarter dissappeared and kept crashing, very weird. Now fine with opera.

---

### Post by bigboy_pdb on 2009-05-03
If you have a live-CD for your current version of Ubuntu you can run the live CD and see how Firefox on the live CD behaves in comparison to your installation. For the firewall problem, you can use the command 'sudo iptables -L' to list the rules for your tables. If you do this with the live CD and your installation, you can copy one and compare it to the other (by using diff, comparing the text files, or both).

---

### Post by DesiArnez6 on 2009-05-03
Did sudo iptables -L, should it be this long, its approaching several pages and consistently going on in the terminal...?

Never mind it stopped, will compare, I have Live CD. Also of the same Ubuntu version. ;)

---

### Post by DesiArnez6 on 2009-05-03
Compared, they were very different,

Everything fine under Live CD

Noticed Firestarter opens when I wasn't connected to anyone, no connection anywhere but continued fluctuating Internet traffic

Until I did this: sudo rmmod iwl3945

All internet traffic came to zero, then I did this

sudo modprobe iwl3945

Interet traffic resumes


Under Live CD, see sudo iptables -L result: [http://rafb.net/p/Sozgzm56.html](http://rafb.net/p/Sozgzm56.html)

Under my regular Terminal see result: [http://rafb.net/p/TqWJ5132.html](http://rafb.net/p/TqWJ5132.html)

Firestarter randomly continues to crash with this other browser, even unlocked itself to blue, without me doing anything, or clicking???, when it does it won't start up again, but as soon as I disable wireless capability, Firestarter immediately opens up on its own fine.

And traffic on port 9091 which I cant block

---

### Post by DesiArnez6 on 2009-05-03
Finally blocked it 9091, (now the port DOES exist?) would be embarssing if this was something simple, but it just seems odd It only existed after I just blocked something on port 443

---

### Post by DesiArnez6 on 2009-05-03
OKay, Firestarter just turned red, (was "locked") Events listed 5 Blocked Attempts at Port 443, should I post in detail?
Then Firestarter button turns blue on its own, I'm typing this while offline (I choose to immediately disconnect) reconnecting now and will paste, sorry for al the posts ...

I locked Firestarter again.

---

### Post by bigboy_pdb on 2009-05-04
I should mention that networking isn't my background so someone from that area of expertise would probably be more helpful, but I'll help you with what I can in the meantime.

Posting the details might help.

You can also use **Wireshark** to monitor your network interfaces in order to see if there's any strange traffic. For example, if you close your web browsers, mail clients, messaging clients, bittorrent clients, and other programs that require a network connection and you still see traffic then that might be an indicator of a problem (depending on what the traffic is).

Based on the log that you posted, it looks like Cablevision is your ISP and you've blocked traffic to/from some hosts. I didn't notice anything wrong with it.

You might want to check launchpad to see if anyone else reported similar problems that relate to Firefox, Firestarter, or iptables.

You can also try reinstalling the Firefox and Firestarter packages.

Based on what you mentioned, I'm guessing you have a wireless card. It's possible that someone's trying to hack your computer through it (or may have already done so), but I think that it's more likely that there's a problem with one of your programs, libraries, or your configuration/setup.

---

### Post by DesiArnez6 on 2009-05-07
> **bigboy_pdb said:**
> I should mention that networking isn't my background so someone from that area of expertise would probably be more helpful, but I'll help you with what I can in the meantime.

Posting the details might help.

You can also use **Wireshark** to monitor your network interfaces in order to see if there's any strange traffic. For example, if you close your web browsers, mail clients, messaging clients, bittorrent clients, and other programs that require a network connection and you still see traffic then that might be an indicator of a problem (depending on what the traffic is).

Based on the log that you posted, it looks like Cablevision is your ISP and you've blocked traffic to/from some hosts. I didn't notice anything wrong with it.

You might want to check launchpad to see if anyone else reported similar problems that relate to Firefox, Firestarter, or iptables.

You can also try reinstalling the Firefox and Firestarter packages.

Based on what you mentioned, I'm guessing you have a wireless card. It's possible that someone's trying to hack your computer through it (or may have already done so), but I think that it's more likely that there's a problem with one of your programs, libraries, or your configuration/setup.

Thanks, I haven't had any problems recently, Ive been using the Live CD only, and also created a new "user" that has no problems, 

I think it was some hacking attempt, which was not fun at all, in fact when I signed off last , my Opera browser began to crash. In another F2 Terminal, I checked and saw an opera plugin eating up alot of memory, so I tried to kill it but couldn't. I then couldn't switch between "users" until I killed opera, then everything went back to normal.

Theres got to be a a way for users to protect themselves from these sort of attacks, Ill try another firewall program, and decided to finally learn iptables the best I can, Thanks for your help. I will try your advice. All good suggestions thanks for following up.

---

### Post by bigboy_pdb on 2009-05-07
One alternate thing that you can do, if you haven't already tried it, is to search launchpad.net for similar problems that are occurring for other people.

There's always a possibility that your problem isn't from a hacker. It could be from a corrupt software installation or configuration (that led to other problems). What MaxIBoy, mentioned about plug-ins is true, and they can be a security risk as well. I generally disable plug-ins that I'm not using regularly. Regardless of the cause of the problem, it would be good practice to look through your system to see if there are indications that it has been hacked.

This document might be helpful:
[http://www.linuxsecurity.com/docs/LDP/Security-HOWTO/](http://www.linuxsecurity.com/docs/LDP/Security-HOWTO/)

Google searches using words such as "linux" or "unbuntu" in conjunction with "compromised" and "security" should turn up helpful results.

An external firewall, such as one built into a router, can also be helpful as a first line of defence against outside attacks.

---

