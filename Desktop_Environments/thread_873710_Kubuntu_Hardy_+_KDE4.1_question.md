---
title: "Kubuntu Hardy + KDE4.1 question"
date: 2008-07-29
forum: Desktop Environments
---

### Post by Zlatan on 2008-07-29
Could someone comment- if Kubuntu Hardy will upgrade to KDE 4.1 by default or it will keep KDE 4.0?
Thank you

---

### Post by usien on 2008-07-29
what version of kubuntu hardy are you talking about?

---

### Post by Zlatan on 2008-07-29
> **usien said:**
> what version of kubuntu hardy are you talking about?

KDE4, of course. KDE3.5 version will keep KDE3.5 for LTS and I'm asking about KDE4 remix- will it get 4.1 or will keep 4.0?

---

### Post by usien on 2008-07-29
seems to be a strange question to me.
you can always install kde 4.1 from the repos, even the alphas and betas were available from the repos, what do you mean by kde 4.1 by default? Hardy is already out and intrepid will have the latest version of kde.

---

### Post by Zlatan on 2008-07-29
> **usien said:**
> seems to be a strange question to me.
you can always install kde 4.1 from the repos, even the alphas and betas were available from the repos, what do you mean by kde 4.1 by default? Hardy is already out and intrepid will have the latest version of kde.

i don't know how to ask you then. have a good day.

---

### Post by NightwishFan on 2008-07-29
I assume the remix cd will have kde 4.04 but it ill upgrade to 4.1, which I believe is already out of the proposed repo and into the standard hardy one. A simple full-upgrade will get you 4.1.

---

### Post by ProbablyX on 2008-07-29
As it says on Kubuntu.org:

To upgrade to KDE4.1:

> 
   1. Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main to your /etc/apt/sources.list.
   2. If you already have the kubuntu-kde4-desktop packages installed, simply type sudo apt-get update && sudo apt-get dist-upgrade and answer the questions in which you are prompted. If you do not have kubuntu-kde4-desktop installed, simply type sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop and answer the questions. Both of these options are to be typed at the command prompt.


---

### Post by NightwishFan on 2008-07-29
He is correct. My mistake, just add the repo, and dist-upgrade. Good luck, and enjoy. :popcorn:

---

### Post by benerivo on 2008-07-29
I don't think you should need to add the launchpad repo just so that it upgrades to 4.1. I think the original question was asking if a default kubuntu-kde4 (remix) installation would upgrade 4.0 to 4.1. I'm not sure it will, but time will tell (!). I'm sure someone in the forums knows how the upgrade protocol works with regards to package versions, and will help.

---

### Post by Zlatan on 2008-07-30
> **benerivo said:**
> I don't think you should need to add the launchpad repo just so that it upgrades to 4.1. I think the original question was asking if a default kubuntu-kde4 (remix) installation would upgrade 4.0 to 4.1. I'm not sure it will, but time will tell (!). I'm sure someone in the forums knows how the upgrade protocol works with regards to package versions, and will help.

yes, that's what i was asking about:)

---

### Post by gjoellee on 2008-07-30
[http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml](http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml)

---

### Post by Zlatan on 2008-07-30
> **gjoellee said:**
> [http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml](http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml)

yeah that was interesting to read, but the original question was about Kubuntu Hardy KDE4 remix- will it upgrade to KDE4.1 with regular repos?
is it really so difficult to understand my question... :confused:

---

### Post by jeremy on 2008-07-30
Zlatan, I think your question is very clear and easy to understand. I am sorry that I cannot give you the answer you need.

---

### Post by jaytek13 on 2008-07-30
You can pretty much guarantee it. The question is really "when will someone package it for the official repos" and that question is a bit harder to answer.

---

### Post by txcrackers on 2008-07-31
Package version numbers are the selection criteria, by default. So, yes, if you add/enable a repository that contains a "higher" version number than the "main" repository(ies), what you will see is the package version from the alternate repo.

If you add the launchpad repo and refresh your package manager, many of the 4.0.x packages will be replaced by 4.1 packages. The trick at this point is to only install 4.1 packages - some of them were renamed from other 4.0 packages and you'd end up chasing down conflicts. There's a couple of apps that haven't quite made the final 4.1 transition (kate, of all things!), so I haven't tried to install them - but the 3.5 versions work just fine.

---

