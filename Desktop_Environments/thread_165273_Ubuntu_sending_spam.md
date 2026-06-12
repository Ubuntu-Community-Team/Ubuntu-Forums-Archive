---
title: "Ubuntu sending spam??"
date: 2006-04-24
forum: Desktop Environments
---

### Post by sas13 on 2006-04-24
I just got a notice from my universities network admins. that my computer is infected by malware and is sending spam: 

> ====================
Supporting Documentation
====================
It was  
observed sending spam.  It is running malware that must be removed.   
Netflow logs showing this activity are listed below. ...

they cut me off from the network!

after calling them and telling them I use Linux, they basically said, "oh we don't know how to handle that".

but they did say the problem is definately a large amount of emails being sent out from my account, and since they don't support linux I'm on my own to find a fix.

I'm using Breezy and Evolution, can't think of any changes I made to my system last week that might be related.

Any ideas?

(sorry if it takes me a while to reply to any responses - I have to go to the library now to get online...)

---

### Post by earobinson on 2006-04-24
If you are running ubuntu stock this is compleat bull, If you have a proxy or anything like that someone could be using your proxy to send spam.

you could also install a firewall (firestarter) is good and only aprove programs that you know are not sending spam

---

### Post by DeadEyes on 2006-04-24
Would this be a large amount of mail coming from your pc or a large amount of mail with your email address as the sender?

---

### Post by sas13 on 2006-04-24
thanks for trying to help out -

The netflow logs they sent me quote my IP, not my email account.

as far as a proxy goes I don't beleive there's anything between me and the university's servers.

Is there anything else that could be happening that an automated system might mistakenly view as a large number of emails being sent?

I don't know very much about these thing so I might not have been asking the right questions when I talked to the technical support guy, is there any information I could ask him for to shed more light?

---

### Post by wylfing on 2006-04-24
It is, unfortunately, going to be almost impossible to help you with this problem. There is a very high probability that someone is cleverly masquerading as your IP address, and nothing you do is going to appease the IT staff. You could even turn your computer off, and they'll still claim it's sending out spam, because "that's your IP address."

There is a small but nonzero possibility that you *are* a zombie, and you should take some steps to lock down more. Install firestarter (as was recommended already) and lock down traffic but good. Or do what I jokingly suggested and turn off your computer for a day. Ask IT if spam is still going out from your unpowered box.

---

### Post by gotdilbert on 2006-04-24
Someone may also be using your computers SMTP relay.

---

### Post by sas13 on 2006-04-24
Thanks for the help, everyone!

wylfing,
actually I found out that I can get online as a guest using the wireless network around here, so the idea of not using "my" account for a day and asking the IT guys if the problem is still there sounds pretty good.
In fact, now that I think of it, I have two seperate IPs - one at home and one in my office that I use the same laptop on (the complaints were only about one)- I could just ask them if they were getting spam from both, right?
when you say "lock things down, but good" do you just mean using firestarter, or more than that?

gotdilbert,
if that is the case (using my SMTP relay) how can I find out for sure/stop it?

---

### Post by wylfing on 2006-04-24
[QUOTE=sas13]
when you say "lock things down, but good" do you just mean using firestarter, or more than that?[/QUOTE]

Firestarter is part of it. If your machine is *comprimised* (i.e., someone else has root access), you're toast already and there is nothing you can do other than wipe the whole thing and reinstall. But assuming that's not the case, per se, and it's just that someone is managing to "use" your box, configuring a firewall to be extremely paranoid could put a stop to it.

Other good lockdown steps include changing your password to one that is cryptographically strong, and shutting down services that you don't need, especially postfix, which could possibly be tricked into sending mail for someone else. (I don't have any idea how, but someone may have found an exploit.)

> In fact, now that I think of it, I have two seperate IPs - one at home and one in my office that I use the same laptop on (the complaints were only about one)

That's probably a good bit of evidence that it isn't you that's causing the problem.

---

### Post by sas13 on 2006-04-25
ok, talked to the IT people again.

It turns out that my office is on a different network administered by someone else, so not having any complaints from there doesn't mean much.

and according to their logs the suspicious trafic stopped after I was quarantined.

I managed to find someone at the helpdesk who knows a little about Linux, he suggested that I might have installed packages that later someone was able to exploit - I don't know exactly what they would be, but this makes some sense to me because I do tend to install a lot of things I see in synaptic just to see what they do, and I guess there is a fair chance I have some network/mail/whatever tools on my system that someone could exploit, or that I unkowingly configured in some strange way (less likely because I hadn't made any changes to my system just before this all started).
They also suggested I look at my own system logs to see if I can find out any more info. I have at least part of the IPs they say the spam was sent to, but honestly I don't know what logs to look at or where to find them.

When the people at the helpdesk went up the tree to the IT security people they basically came back with - you've gotta do a complete reinstall, since the comprimise has been logged for several days (and we don't want to spend the time looking at your case in depth).

As much as I hate doing a reinstall without knowing what the problem originated from, I might just do that in the interest of saving time (and it sounds like a good time to upgrade to Dapper)

---

### Post by wylfing on 2006-04-25
[QUOTE=sas13]according to their logs the suspicious trafic stopped after I was quarantined.[/QUOTE]

Wait a minute. They blocked your IP address and the traffic from that IP address stopped. O_o. They're smart ones, all right. What else did they think would happen? The only way this is going to be properly tested is if they grant full network access again but you don't connect your computer to the net. Trick them into doing the test: just tell them you've done a reinstall and everything's fixed.

In addition, bring your computer to your office (where you have net access) and install firestarter. After it is installed, unplug from the network so that you are 100% sure no one but you is logged in. Configure firestarter for total net blockage, and watch its activity screen. That will tell you if something on your system is trying to send packets out into the world. 

If no rogue software is generating traffic, then either you are comprimised or there is packet spoofing going on. Having IT re-enable your network access but leaving your computer off the network will test which of these two cases is true. If the bad traffic resumes but you aren't connected -- someone is spoofing, and you need to let the IT folks know that. If the traffic does *not* resume, then you do a wipe and reinstall.

> I managed to find someone at the helpdesk who knows a little about Linux, he suggested that I might have installed packages that later someone was able to exploit - I don't know exactly what they would be, but this makes some sense to me because I do tend to install a lot of things I see in synaptic just to see what they do

No, it actually doesn't make much sense at all. Although the probability of it is greater than zero, it is still quite remote. I think there is a far higher chance that someone is spoofing packets on the network. Do these tests to find out which it is.

---

### Post by sas13 on 2006-04-25
thanks wylfing, that makes a lot of sense.

I'll set up firestarter and unplug right now and post back with results.

---

### Post by sas13 on 2006-04-25
ok,

installed firestarter, told it to block all outgoing connections, and watched the log. I tried this both with the network cable plugged in and unplugged.

when the cable is unplugged there's nothing doing - probably because my laptop recognizes that it's not online.

plugged in there were tons of outgoing SMTP events, it seems that they were all to IPs "whois " identified as belonging to google. these appear sometimes up to every 3 seconds!! (although sometimes there might be a few minutes of inactivity)

this led me to check the IPs in the original messages from our IT office - and most (though not all) of those IPs also belong to google.

so this got me thinking - I had evolution set up to forward all of my incoming and outgoing email to a gmail account, which I use as an archive. I think what might be happening is that evolution is reapplying the filters to everything in my inbox which means sending out all those emails... 

anyway I just cancelled that rule in my filters and I'll run the trick with firestarter again to make sure it went away!

thanks wylfing!! I hope I've caught it now.

---

### Post by sas13 on 2006-04-25
yup, disabling the filter seems to have fixed it.

if I tell firestarter to block all outgoing traffic, enable that filter rule and then tell evolution to filter my inbox, I get a million SMTP attempts.

switch off that one rule, tell evo to run the filters and the only thing that firestarter logs is evo' s few imap attempts to check for new messages.

the strange thing here is that I had that filter set up for months without complaint. The only big change I've made recently is switching from using GNOME to xfce4, but even that was several weeks ago and I don't see how that would have anything to do with it.

I guess maybe the IT people have recently changed the way they look for spam on the network.

anyway they want me to bring my laptop in to them tomorrow to confirm the problem is resolved before they remove the quarantine - now that I told them it's fixed they want me to come in, but while I was fishing for the problem they said not to come in with a linux box 'cause they don't support it...

thanks again wylfing for helping me out!!

ubuntu forums rock.

---

