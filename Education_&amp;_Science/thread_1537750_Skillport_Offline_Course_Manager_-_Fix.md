---
title: "Skillport Offline Course Manager - Fix"
date: 2010-07-24
forum: Education &amp; Science
---

### Post by arm-c on 2010-07-24
This post is intended to assist those people that may be trying to utilize the Skillport Offline Course Manager (SCM) to download learning courses to use when you have no reliable internet connection.

The current software that will download to your computer from their site is heavily Java based.  It appears to be configured slightly wrong.

They key elements to getting the application to run are to update some of the paths in the OCMStart.sh script.

I am going to post those scripts here for others to use.  Ensure that you set the permissions to execute after copy them to the ./Skillport/Client folder.

You will also need to set the execute permissions for the desktop icons if you plan on launching from them.

Hope this helps.

ARM-C

---

### Post by bunny12 on 2010-07-28
I am going to post those scripts here for others to use. Ensure that you set the permissions to execute after copy them to the ./Skillport/Client folder.

---

### Post by arm-c on 2010-07-29
I use the above scripts on all of my systems, but I had a situation where my netbook, for whatever reason, would not acknowledge that the skillsoft offline course manager (aka: skillsoft course manager) was installed and kept asking me to install.

The technical support at Skillsoft was very poor in their knowledge and once it was escalated to next level, they essentially told me to install an approved OS (ie: Suse / OpenSuse).  For posterity sake, the links I was provided to view and the text of the reply follow.  My subsequent post will have my solution to that peculiar (and I am not sure it is reproducible) issue.  First, the reply:

[INDENT]Hello A.,

As per our conversation please see the below links which outlines SkillSoft player requirements and site requirements.  Once there is a valid system configuration we can continue to troubleshoot any further courseware issues.

[http://documentation.skillsoft.com/index.htm?toc.htm?20891.htm](http://documentation.skillsoft.com/index.htm?toc.htm?20891.htm) 

[http://documentation.skillsoft.com/index.htm?toc.htm?21054.htm](http://documentation.skillsoft.com/index.htm?toc.htm?21054.htm)

Regards,

A.H.

Tier II Technical Support
SkillSoft Corporation[/INDENT]

---

### Post by arm-c on 2010-07-29
SOLUTION:

Notes for Ubuntu users that are having trouble.

**preliminary preparation:**  
[LIST]
remove the default OpenJDK packages (complete removal)
install sun-java and the sun-java plugin from the official repository
run the browser tests ([http://java.skillport.com](http://java.skillport.com)) 
update the popup bocker with the requisite sites
[/LIST]

**General Installation Information:**

1.  Install the Skillport Course Manager from the website. It is cryptic on this, but it happens automatically when you select download a course from its overview page.

2.  Edit (or replace) the OCMStart.sh (located default in "/home/<user_profile_name>/Skillsoft/Client" folder)file has several broken paths that point to the java components and it also points to Konquerer instead of FireFox as the browser.  The files are attached to the first post in this thread.  Ensure they are set to be executeable (in the file manager, you right click file, select properties, then select permissions and check box for executeable)

3.  After that, everything should work fine.  If it doesn't, check the Learning Management System (LMS) post URL settings... on one of my computers, it was different from the other three working systems (I don't know why....).  The setting I used:
```
pvsp70armyabe.skillport.com/skillportbe/scusarmy/AICC.rbe
```

4.  If they are having the issue where trying to download after you installed the SCM/OCM you are still told you need to install the software, read on for that fix.:

a.  When a dialog pops up saying course manager is not installed and to click OK to install, **CLICK CANCEL**.  The popup window stays open.

b.  Right click on the popup window and select view source.  I did a *select all* and pasted into gedit.  Scroll way down on to the bottom (or search) for "var commandSCM_URL"  For me, that was located on line 854.  The value of the commandSCM_URL is as follows.  _*YOU NEED TO USE YOUR OWN CODE, as it is tailored to the user...*_

*"https://pvsp70armyabe.skillport.com/skillportbe/scusarmy/Cmd.be?cmd=SSDownloadSpcsf&template=ssdownloadocm.tpl&sessionid=<yourUserName.CODEXXXXX=pvsp70armyabe.skillport.com/skillportbe/scusarmy/Result.rbe&contentRoot=content/player&courseNumber=259930_eng&contentType=application/skillsoft-ocm&ocmCommand=DOWNLOAD&x508=0"*

c.  Copy the URL between the quotes.

d.  Open Firefox, Log into Skillport.

e.  Open a new tab.  Paste the URL from step 4.b. (*do not include the ""*) above into the URL Location Bar and press enter.

f.  The download window will open.  Select "Open With" and browse to the home/<user_name>/Skillsoft/Client/OCMStart.sh file and select it.  Select "Always Do this Action" for files of this type.  Click OK.

g.  SCM/OCM should open and then you should be able to select and download the course from inside the SCM/OCM.

That is it.  It should all work fine now.  

**I tested this out a couple of ways with the following results:**
 - The downloads after this process worked smoothly and as expected.
 - Logging out and back in produced the expected result (the SCM synchronization took place).
 - I am able to play courses offline now.

**Things I did that had no effect:**
 - Uninstalled Firefox and reinstalled.
 - Removed all firefox add-ins
 - returned to default theme in firefox
 - unistalled / reinstalled Skillsoft Course Manager (SCM / OCM)
 - deleted all of the skillsoft folders. (essentially an uninstall).
 - moved the __skillsoftinstalled.class file to a different directory (suggested by Skillsoft Tech Support even though the systems that were working fine with same OS didn't have that file in the directed location).

I hope this is helpful.  Sorry for the poor writing style, but it is late and I am tired.  Happy 'Buntuing' to all.

---

### Post by shade82000 on 2010-10-09
Thank you so much for this guide!  It has been so helpful for me!

I don't know too much about Linux and had to keep Win XP just for the SCM but now I can completely dispose of XP :)

I did notice it was previously looking for Konqueror and I was going to install Kubuntu just for the SCM, but I guess it may not have worked anyway given that there were also problems with the Java location.

At least you got a half response from Skillsoft, they just told me 'sorry we wont support that.'  Their software isnt the best and their install instructions are useless.

Your tech expertise astounds me, I wouldn't have been able to fix this on my own.  Thanks again!

---

### Post by shade82000 on 2010-10-13
Hey Arm-c,

Have you had any problems with running different sections of course material?

I downloaded all 11 sections of the CompTIA Network+ 2009 course but SCM always takes me to the first course section that I downloaded, regardless of which one I try to run.

I'm not sure if, once the online progress had been updated, I could delete the first section and let it automatically start the second section and so on, or if I would need to delete them all and just download them one at a time, but I will give it a try tonight.

Just wondering if you have experienced anything similar?

---

### Post by shade82000 on 2010-10-13
Update:

I just went online to sync my course progress before removing the first course subject but the SCM seems to work properly when online.  I can start any course I like or go back to a bookmark in a course.

But, when I take it offline again, it will only ever let me go back to the last course that I was on when it was last online, no matter which course I try to load.

I guess it's not a major problem for now as I only use it for 90 mins each day on the train so I can always start the next course online and then go back to it on the train.

At least this is a temporary workaround.

I'll still look into it further and post here if I find a fix.

---

