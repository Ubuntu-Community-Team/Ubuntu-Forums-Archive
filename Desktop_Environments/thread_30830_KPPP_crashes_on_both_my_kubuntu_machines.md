---
title: "KPPP crashes on both my kubuntu machines"
date: 2005-04-30
forum: Desktop Environments
---

### Post by fgeiger on 2005-04-30
At the moment KPPP connects it crashes telling me, that pppd has unexpectedly died with exit code 1. I observe this on both my kubuntu machines, but NOT on my SimplyMEPIS 3.3. machine (MEPIS is another KDE distro). All machines run the same pppd version and KPPP is conf'ed the same way (same ISP, user, passwd).

What can I do to investigate this further (I am a Linux newbie!)? Or is this behavior known for kubuntu and does a solution exist then already?

Many thanks in advance and kind regards
Franz GEIGER

---

### Post by jodef on 2005-04-30
Exit error code 1 is an authentication problem see my post here:

[Kppp Error](http://www.ubuntuforums.org/showthread.php?t=30808)

---

### Post by fgeiger on 2005-05-01
Thanx a lot, Johann! I am writing these lines already from my kubuntu machine.

Many thanks again and kind regards
Franz GEIGER


P.S.:

After a few kubuntu hours I have got the impression, that k/ubuntu could be newbie-friendlier. 

I am, e.g., not able to switch to language German, despite the fact that kynaptic is telling me, that the language-de package is installed. In the Control Center German is not listed as an "Other" language.

Second, as I wanted to switch from the barely usable kynaptic to synaptic (why the heck had there to be invented another one?) by entering sudo synaptic on a console, I get a "sudo: synaptic: command not found". You guess it, I am stuck again :-(

---

### Post by fgeiger on 2005-05-02
I've got to manage it :-)

For all other newbies out there:

- Edit /etc/apt/sources.list to enable apt to access Internet:
sudo vi /etc/apt/sources.list

- sudo apt-get update

- sudo apt-get install synaptic

- After download has completed start synaptic from a console by entering sudo synaptic as doxed or start it from the GUI: System->Synaptic.

Kind regards
Franz GEIGER

---

