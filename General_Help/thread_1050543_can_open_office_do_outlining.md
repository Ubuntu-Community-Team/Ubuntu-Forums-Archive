---
title: "can open office do outlining?"
date: 2009-01-25
forum: General Help
---

### Post by crimlaw on 2009-01-25
for school I have to outline my notes.  I like the numbered list with the sub parts and then sub sub parts.  However, after coming to open office after using Word, I have found that outlining is not as easy and is causing quite the headache.

When I start an outline, I go to "Bullets and Number" and pick an outlining scheme, and while I am working with it, it does the job.  However, when I exit and then reopen my document to continue working, it gets all messed up.  The indents are all off, sometimes when I tab over for a subset, the bullet stays where it is and the cursor indents.  Then the numbers and letters won't match up.  And I am constantly changing the indents with the ruler at the top of the screen.  It just seems like it is constantly changing.

Is there any fix to this, or is this just somewhere where Open Office lacks to Word?

Thanks!!!

---

### Post by Temposs on 2009-01-25
I have not experienced this, personally. Can you tell please what version of Open Office you're using?

---

### Post by crimlaw on 2009-01-25
latest version I can find 3.0

---

### Post by Temposs on 2009-01-25
If you are using Ubuntu 8.10, why don't you try Open Office 2.4.1, which is the current supported version. I just tried the operations you indicated gave you problems, and they work for me just fine.

---

### Post by crimlaw on 2009-01-25
I already upgraded, how to I reverse the upgrade?

---

### Post by Temposs on 2009-01-25
I think that the easiest way is to reinstall open office using synaptic package manager. I think that should install the version from the repositories. Tell me how it goes...

---

### Post by crimlaw on 2009-01-25
stick with me her, beginner, to do this, I go into synapic package manager, search for open office, the remark all of the squares already marked for open office and click apply?

---

### Post by Temposs on 2009-01-25
Yeah, check that the "latest version" is 1:2.4.1-11ubuntu2.1. The "installed version" should be something like 3.0. Then for all the open office packages that you have installed, do "mark for reinstallation". Tell me how it goes.

---

### Post by crimlaw on 2009-01-25
when I look at synaptic, it says "installed version" 1:3.0.1.  Would that work, or is that the latest version that I don't want?

---

### Post by Temposs on 2009-01-25
That's what I expect. And the "latest version" should be 1:2.4.1-11ubuntu2.1.  If that's the case, try the reinstallation. After you do the reinstallation, the "installed version" should be 1:2.4.1-11ubuntu2.1. Tell me how it goes.

---

### Post by crimlaw on 2009-01-25
na, did not work.  I still have 3.0.  I checked off all of the boxes already colored and hit remark for installation (or mark for reinstallation).  Nothing happened.

---

### Post by Temposs on 2009-01-25
OK, I think we need to change some settings. In Synaptic, choose the Settings menu, then choose Preferences. Then click the Distribution tab. Choose "Prefer versions from", then choose "intrepid-updates" from the drop down menu. Then click Apply and OK. Then retry the reinstallation again. Tell me how it goes.

---

### Post by crimlaw on 2009-01-25
no, that did not work either.  Should I go back into synaptic and change my settings back to what they were before?  

What if I go into Add/Remove under the "applications", uncheck open office in there,that should remove it, then go back to add/remove, and reinstall.  Would that work?  

If not, no worries, maybe I just have to keep working with it.

---

### Post by Temposs on 2009-01-26
You can change the settings back to whatever it was on.

Add/Remove won't let you remove everything. I was hoping this wouldn't be necessary, but here goes. Open a terminal and type this:

```
sudo apt-get clean
sudo apt-get openoffice.org*
```

Now, when you do this, pay attention to all the packages being uninstalled. For me, it looks like this:

```

aspell aspell-en dictionaries-common gnome-spell hunspell-en-us
  language-support-en language-support-translations-en
  language-support-writing-en myspell-en-au myspell-en-gb myspell-en-za
  openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-evolution
  openoffice.org-filter-binfilter openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-hyphenation
  openoffice.org-hyphenation-en-us openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-officebean openoffice.org-report-builder-bin
  openoffice.org-style-andromeda openoffice.org-style-human
  openoffice.org-style-industrial openoffice.org-thesaurus-en-au
  openoffice.org-thesaurus-en-us openoffice.org-writer
  openoffice.org-writer2latex python-uno thunderbird-locale-en-gb
  ubuntu-desktop wbritish

```

now, make sure after you remove everything that you install each one of those packages I listed and any more that are listed for you. You can just find them in synaptic package manager. This should clear out any trace of open office 3.0. Tell me how it goes.

---

### Post by crimlaw on 2009-01-26
I have to admit, I am always nervous about removing things through the terminal.  I have no idea what I am doing when I open a terminal, and I am worried that once I remove it, it won't come back.  However, when I get out of class tonight, I will most likely give it a try.  

Thanks for the help, I will be sure to keep you posted.

---

### Post by Temposs on 2009-01-26
It's really the exact same as removing it in Synaptic. The reason for using terminal is to run the "clean" command first, really. So, at least run that first command. You could remove all of the open office packages through synaptic, if you want.

---

### Post by crimlaw on 2009-01-27
I opened the terminal, entered: 

sudo apt-get clean
sudo apt-get openoffice.org*

and it said "E: invalid operation openoffice.org*

I tried it without the * and got the same response.  

What did I do wrong?

---

### Post by Temposs on 2009-01-27
bah, stupid me

```
sudo apt-get remove openoffice.org*
```

---

### Post by ubuntu27 on 2009-01-27
Visit [http://openoffice.blogs.com]("http://openoffice.blogs.com/")/ to learn about how to use OpenOffice.org
You will find neat tricks in there.



A new version of OpenOffice.org has been released TODAY. Let's hope that the bug you have encountered is fixed in this bug-fix release. 

[Here is the Release Note]("http://development.openoffice.org/releases/3.0.1.html") (Change Log) of the new 3.0.1

[http://development.openoffice.org/releases/3.0.1.html]("http://development.openoffice.org/releases/3.0.1.html")

**************************

From: 	John McCreesh
To: 	announce AT openoffice.org
Subject: 	[ooo-announce] OpenOffice.org 3.0.1 generally available
Date: 	Tue, 27 Jan 2009 08:12:09 -0000 (GMT) (00:12 PST)

The OpenOffice.org Community is pleased to announce the immediate
availability of OpenOffice.org 3.0.1. This release fixes a number of minor
issues reported with OpenOffice.org 3.0, released on October 13th last
year. Although minor releases normally do not include new features, there
are two points of interest: enhanced support for grammar checkers, and an
increase in the number of words held in personal word lists to  30,000.

A full list of all the issues fixed may be found in the developers'
release notes at [http://development.openoffice.org/releases/3.0.1.html]("http://development.openoffice.org/releases/3.0.1.html")

OpenOffice.org 3.0.1 is available now from [http://download.openoffice.org]("http://download.openoffice.org")
in over 90 languages and for all major platforms.  For the availability of
further languages and platforms please check
[http://download.openoffice.org/other.html]("http://download.openoffice.org/other.html")

The next release of OpenOffice.org to contain significant new user
features will be OpenOffice.org 3.1, scheduled for general availability at
the end of March.

The OpenOffice.org Community

--
Developers - join us! see [http://council.openoffice.org/developers.html]("http://council.openoffice.org/developers.html")

---

### Post by crimlaw on 2009-01-27
when I start up Openoffice, it says 3.0.  However, when I went to "help" "about openoffice," it says 3.0.1.  Look like I already have the updated version.  No bug fix.  I still plan to give you idea a try, but I might also just stick with the version I have and wait for March's update.

I will keep you posted if I try to remove and reinstall.  

Thanks

---

### Post by crimlaw on 2009-01-28
let me ask you one more question before I downgrade, if you don't mind.  Is there any reason to keep 3.0.1?  Besides my outlining problem, am I going to lose something important by downgrading.  Is there a serious bug that was fixed with the new version?

---

### Post by ubuntu27 on 2009-01-28
> **crimlaw said:**
> let me ask you one more question before I downgrade, if you don't mind.  Is there any reason to keep 3.0.1?  Besides my outlining problem, am I going to lose something important by downgrading.  Is there a serious bug that was fixed with the new version?

In my opinion there is no reason to keep using OO.o 2.4.  
OpenOffice.org 3 brought new features, not just bug fixes.

See the following site in order to new what's new in OpenOffice.org 3


[URL="http://www.openoffice.org/dev_docs/features/3.0/"]OpenOffice.org 3.0 New Features
[/URL]



You can take a look at [Change Log]("http://development.openoffice.org/releases/3.0.1.html") for OpenOffice.org [3.0.0]("http://development.openoffice.org/releases/3.0.0.html") and [3.0.1]("http://development.openoffice.org/releases/3.0.1.html") to see if there is any serious or show-stopper bug for you.

Here is mine:

The bug where when you want to add a frame [Insert menu/ Frame] in OpenOffice.org 2.4.x it will not anchor wherever you wanted it to be. 
For example, when you tell it to put the frame surrounding the whole page or sheet, it will just ignore it and  insert a SMALL frame that you will have to drag it manually to make it anchor on the page.
Really annoying. 
This was fixed in OpenOffice.org 3.0

---

