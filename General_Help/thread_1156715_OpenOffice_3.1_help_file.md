---
title: "OpenOffice 3.1 help file"
date: 2009-05-12
forum: General Help
---

### Post by ScottMartin on 2009-05-12
In trying to use oo3.1, I tried to open the help file and it complains that I do not have openoffice.org-help-en-us installed. I do have it installed.
I can see it in synaptic and I reinstall from console.

I have went into opions/settings/language and setup and English-US just in case.

I even removed OO3.1 and reinstalled the suite from scratch. This happens on 2 difference PCs's

How hard is it to load help file?

Any ideas?

Regards,
Scott.

Ubuntu 8.10/amd64
oo3.1

---

### Post by dgermann on 2009-05-12
Scott--

Hope you get an answer--I'm having the same problem, on three separate computers, all 8.04.

---

### Post by mikewhatever on 2009-05-12
What version is the installed package openoffice.org-help-en-us? Does it match the version of Open Office?

---

### Post by dgermann on 2009-05-12
mikewhatever--

Insightful question!

openoffice.org-help-en-us shows 1:2.4.1-1ubuntu2.1 in Synaptic.
openoffice.org-writer shows 1:3.1.0~rc2-1ubuntu1~hardy1.

So they do not match.

Now in synaptic, the help file only shows as another availability 1:2.4.0-3ubuntu1 (hardy). If I'm reading this all correctly, there is no help version available for 3.1.0 (nor for 3.0.1 where I had help).

So what do I do to get the 3.1.0 version? Maybe it is not available for the rc2? (I'm guess that means release candidate.)

Thanks for giving me more clues!

---

### Post by SPrevatt on 2009-05-13
I'm having the same problem in Jaunty.

---

### Post by mikewhatever on 2009-05-13
It looks like the installation files for OO 3.1 didn't include the help file. Did you get the files from [http://download.openoffice.org?](http://download.openoffice.org?) OO 3.1 is officially released, so why is it rc2?

---

### Post by SPrevatt on 2009-05-13
I followed this howto:

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

When I ran into the problem, I went to the synaptic package manager and reloaded openoffice.org-help-en-us to no avail.  Still the same problem.

---

### Post by SPrevatt on 2009-05-13
I noticed that the howto above assumed an installation for Great Britain, so I issued the following command from the terminal:

sudo apt-get remove openoffice.org-help-en-us

and then installed openoffice.org-help-en-us from synaptic package manager again.  This didn't work either.

---

### Post by SPrevatt on 2009-05-13
Sorry my posts haven't been more complete and concise.

OpenOffice.org Calc application reports OpenOffice.org 3.1.0
Synaptic reports as installed version of openoffice.org as 1:3.1.0-1ubuntu1~jaunty1

Synaptic reports as installed version of openoffice.org-help-en-us as 1:3.0.1-9ubuntu2
Synaptic reports as latest version of openoffice.org-help-en-us as 1:3.0.1-9ubuntu2

---

### Post by ScottMartin on 2009-05-13
My versions match as I see it.

package: openoffice.org-core 
Synaptic: 1:3.1.0-1ubuntu1~intrepid1

package: openoffice.org-writer
Synaptic: 1:3.1.0-1ubuntu1~intrepid1

package: openoffice.org-l10n-common
Synaptic: 1:3.0.1-1ubuntu1~intrepid1

package: openoffice.org-help-en-us
Synaptic: 1:3.0.1-1ubuntu1~intrepid1

All oo3 packages seem to be at 1:3.0.1-1 as expected.
(err, what I should have said is that all installed version match latest versions), but yes there is difference now that I look at it standing over here. ;)

Regards,
Scott.

---

### Post by mikewhatever on 2009-05-13
Not sure if it matters, but **3.1.0** is obviously not equal to **3.0.1**.

---

### Post by plamen_todoroff on 2009-05-13
ScottMartin, you don't see right. They don't match. Look at the build status here [https://launchpad.net/~openoffice-pkgs/+archive/ppa]("https://launchpad.net/~openoffice-pkgs/+archive/ppa"), as I suppose you use that PPA. The language packs are not ready yet. Failed to compile 2 times now, don't know the reason.

---

### Post by ScottMartin on 2009-05-13
ok, let me be more specific. I see that there is a difference, but 'what I meant to say was ...' lol, that my -installed- version matches the -latest- version in synaptic.

Perhaps this is the problem as you mention ... that the launguage pack has failed compile and that is my/our problem.

Regards,
Scott.

---

### Post by mikewhatever on 2009-05-13
Synaptic shows whatever packages you have installed and their versions. Looking at one of the previous posts, there is an obvious version mismatch between **openoffice.org-core** and **openoffice.org-help-en-us** packages. In other words, the installed version of openoffice.org-help-en-us does not match the installed version of openoffice.org-core.

---

### Post by SPrevatt on 2009-05-13
So, if I understand correctly, when the 64-bit version gets compiled, we'll be able to use the update manager to bring in the appropriate files which should fix our problems, right?

---

### Post by jordanchap on 2009-05-18
Any word on this?  I still cannot access the help files.  I just want to know how I can get the darn quicklaunch back.

---

### Post by robc02 on 2009-05-29
I have just installed the latest OO0 3.1 updates via Update Manager, and my help files now work. 
Just to recap, I am using Openoffice 3.1 on Hardy. I updated my sources.list file to include the appropriate repository so that I would pick up any updates as they happened.

---

### Post by sim909 on 2009-05-29
> **robc02 said:**
> I have just installed the latest OO0 3.1 updates via Update Manager, and my help files now work. 
Just to recap, I am using Openoffice 3.1 on Hardy. I updated my sources.list file to include the appropriate repository so that I would pick up any updates as they happened.

Same goes for Jaunty, all is ok now.

---

