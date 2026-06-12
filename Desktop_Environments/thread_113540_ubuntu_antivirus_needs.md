---
title: "ubuntu antivirus needs"
date: 2006-01-06
forum: Desktop Environments
---

### Post by Doc504 on 2006-01-06
When using ubuntu on the internet, what antivirus program is needed?:confused:

---

### Post by CarlosinFL on 2006-01-06
Um..none. You're using Linux. You don't need to be concerned.

---

### Post by Tuf on 2006-01-06
This is an interesting question and one I am curious about as well. I understand Linux is not as vulnerable as Windows but what are the probabilities of encountering some malacious Linux code?  And if you did how damaging would it be?

---

### Post by CarlosinFL on 2006-01-06
Any problems are detected immediatley and patched in the kernel usually in 24 hours rather than 2 years for a Windows SP.

I have been using Linux since 2001 and surf a lot of crap and have never had any problems. Anti-virus software is just not needed in Linux since most .exe files or imbedded registry code is useless in Linux.

Just sit back and enjoy the fact you're using Linux.

---

### Post by dcstar on 2006-01-06
[QUOTE=Doc504]When using ubuntu on the internet, what antivirus program is needed?:confused:[/QUOTE]
I use ClamAV to scan my incoming e-mail messages in Evolution, so I know what Windows crap is coming into my system (and I have it identified and deleted immediately!).

---

### Post by nalmeth on 2006-01-06
yes, I surf quite liberally, and have not gotten caught up with any nasty bugs. I still worry though. I think I might backup my home folder, and pursue a linux virus one day. I'd like to see it happen. It seems too perfect. Can anyone share an anecdote regarding a linux virus?

---

### Post by dcraven on 2006-01-06
Classic malware like worms and viruses are an oddity in Linux, yes, but one should still remain careful when downloading and running untrusted software. I could write a 6 line program that hoses your machine and post it here saying that it is a virus scanner but it must be run as root. Several machines would get hosed before someone posted a follow up warning in the thread.

There is a certain level of trust that we in the Linux world put on our software developers that I'm afraid will be short lived if popularity continues to grow at its current rate. Hopefully it won't be a huge deal, and I'm not trying to be a nay sayer or trying to say the trust is misplaced because it's not. I'm just saying that if we grow in market share, we may end up being a pretty easy target for a short while. It's more of a social vulnerablility than a technical one. I can't say that I review the source code of every program I download, but I try to download from reliable sources if possible. The repositories are quite safe for example.

Cheers,
~djc

---

### Post by nalmeth on 2006-01-06
Ahh yes, you refer to social engineering viruses. People that trick you into allowing them full admin priviledges.

I think what the last poster is saying, is that Ubuntu is very safe from convential windows viruses, and viruses in general, but the owness is on you to look out for you own safety with common sense and caution. Anyone could be tricked if the joker is ingenious enough. 

The key with linux is the the admin or 'root' user is disabled by default. In windows, you are running as a user and an admin user, so it is very easy for a malicous piece of code to do whatever it likes to your most important and integral files.

So if you have a router, don't be too worried about a soft-firewall. Pick up an anti-virus program if you would like some assurance - however, I don't know who runs them, or how hard they are looking.

---

### Post by shade11 on 2006-01-06
I am using clamAV as well. I thin that even though you are using Linux you will still need an antivirus just incase.

---

### Post by endy on 2006-01-06
Correct me if I'm wrong but there is no virus for Linux. What you *could* get is a "root kit" which is about as bad as it gets but at the same time quite unlikely. For more information on root kits see [Wikipedia]("http://en.wikipedia.org/wiki/Root_kit").

If you only run Linux then there is no need to scan for Windows viruses as they won't work on Linux, however there is no need to forward on Windows viruses to other people either ;)

If you are truly worried that you are being targeted by malicious types (AFAIK you'd pretty much have to be targeted specifically) then please see  tools like [Rootkit Hunter]("http://www.rootkit.nl") and  [chkrootkit]("http://www.chkrootkit.org/") (chkrootkit is availble via apt / synaptic).

Being secure is a good thing and keeping an eye on things is always good but, the chances of something bad happening to you on Linux is ALOT lower than when running Windows in my experience. Surf in peace :)

---

### Post by nalmeth on 2006-01-06
ah interesting! I've never heard of rootkit. I needed to know there was something to look out for. This doesn't look terribly dangerous though.

---

### Post by holiday on 2006-01-06
If your computer is exposed to the internet i.e. if it is offering any services such as a ssh, or ftp ... then you are vulnerable to intrusion. I can get 500 hits a day on my ssh. These seem to be automated attempts using standards like root, admin, test, guest and common names such as susan, stephen, bruce and so on with probably simple passwords. So I disable root login, use unlikely usernames and  good passwords. 

One of the linux systems I worked with a few years ago was owned by others for nearly six months. The attackers recompiled the kernel and turned the machine into a porn relay in the company's afterhours. 

So - although linux machines are not as often compromised as Windows machines, you should be aware of your vulnerabilities and take reasonable, simple precautions. Attackers are looking for an easy mark, so unless you have very valuable data or resources, the simplest precautions will be adequate.

---

### Post by r4ik on 2006-01-06
It not the question if there are virussus imo there are,but when bigger if not huge numbers will pop up since Ubuntu and Linux is growing so fast.
It will become an more and more interesting target.

---

### Post by endy on 2006-01-06
[quote=holiday]If your computer is exposed to the internet i.e. if it is offering any services such as a ssh, or ftp ... then you are vulnerable to intrusion. I can get 500 hits a day on my ssh. These seem to be automated attempts using standards like root, admin, test, guest and common names such as susan, stephen, bruce and so on with probably simple passwords. So I disable root login, use unlikely usernames and  good passwords. 

One of the Linux systems I worked with a few years ago was owned by others for nearly six months. The attackers recompiled the kernel and turned the machine into a porn relay in the company's afterhours. 

So - although Linux machines are not as often compromised as Windows machines, you should be aware of your vulnerabilities and take reasonable, simple precautions. Attackers are looking for an easy mark, so unless you have very valuable data or resources, the simplest precautions will be adequate.[/quote] 
I completely agree however, as far as I'm aware there are hardly any services running on Ubuntu by default so we are at least shielded by the more common and automated attacks. Still, you are right that there is no substitution for vigilance (and a good firewall) :)

Here is a nice simple and fast test for what the world sees of your computer:

[Shields up!]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

