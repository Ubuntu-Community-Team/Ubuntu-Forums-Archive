---
title: "[Ubuntu] How to activate Excel Analysis Toolpak for Excel 2007 running via WINE"
date: 2009-05-21
forum: Education &amp; Science
---

### Post by amylase on 2009-05-21
As title thanks.

I successfully installed Excel 2007 and it runs smoothly. Problem is Excel doesn't come with Excel Analysis Toolpak activated. I attempted to activate it by the follow:

   1.  Click the Microsoft Office Button Button image, and then click Excel Options.
   2. Click Add-Ins, and then in the Manage box, select Excel Add-ins.
   3. Click Go.
   4. In the Add-Ins available box, select the Analysis ToolPak check box, and then click OK.

At this stage Excel 2007 spits out an error and quits. 
Normally if Analysis Toolpak is installed successfully it would come up in Analysis group on the Data tab.
Not surprised with the error during activation, Data Analysis command does not appear.

Did any one get the toolpak to work on their Excel 2007 running in WINE?

Thanks.

---

### Post by s6long1 on 2009-09-26
I'm having the same problem with Office 2003 under Wine. Its all installed locally, but when I go to load the analysis toolpak, all I get is a blank error box with an OK button. pressing it does nothing except make the box go away. I need this for school, so it would be great if someone was either working on making it work with wine, or adding this functionality to OpenOffice...

---

### Post by samden on 2009-09-27
s6long1, depending what you actually want to do, you're probably far better off using a dedicated stats program such as R than a spreadsheet add-on.  

If you have a specific school course built around the MS product, and you've never done stats before, that won't be much help. But if you are wanting to do proper statistical analysis, Linux is just as good as Windows, if not better, provided you are prepared to learn the real tools.

---

### Post by marcbuntu on 2009-09-28
Actually I have the same problem as Amylase. I can't find a way to install adds-in in microsoft excel when running it on ubuntu 9.04. I know there are programs much more powerful than these adds-in but it's compulsory for me to use them for my school...
If someone could help me...
Thanks a lot!!

---

### Post by gunksta on 2009-09-30
Before offering any ideas here, I should point out that I have never used this Excel plug-in. That being said, it seems reasonable for me to assume that the reason you are getting an error is that the installation routine/plug-in is looking for a Windows component that _should_ be there.

Wine is not a complete reincarnation of the Windows stack, although it is incredible. Some software, like MS Access require things that are not part of Wine but ARE part of MS Windows. Thus, Access does not appear to work when you first install it, although it will work (mostly) with a little help.

[Winetricks]("http://wiki.winehq.org/winetricks") enters the scene and makes this much much easier.

For what it may or may not be worth, here is something that I wrote regarding using MS Access under Wine (using Winetricks).

[http://ubuntuforums.org/showthread.php?t=1101477](http://ubuntuforums.org/showthread.php?t=1101477)

Good Luck!

---

### Post by wgarcia on 2010-04-29
If you can move from Excel to Openoffice.org Calc, I wrote a set of macros to perform descriptive statistical analysis with Calc. It can be found in:

[http://sourceforge.net/projects/odstatistics/](http://sourceforge.net/projects/odstatistics/)

---

### Post by HydrologyGuy on 2010-04-29
Let me put in a plug for gnumeric. It has pretty good statistical add-ins. Although I do 99%+ of my statistical analysis work in R, gnumeric is useful for quick and dirty jobs. Also, it exports graphs in all kind of formats including eps.

Most importantly, because it's Open Source it's possible to check its source code -- how can you ever be sure what Excel is doing?

---

### Post by linux fanatic on 2011-10-24
I have resolved this issue and I am afraid I cannot concur with those who support linux alternatives to Excel's Analysis toolpak.

There is a file that is not properly installed when you use wine to install Excel. That file is ANALYSIS32.XLL. It is the specific add-on file for that toolpak. When you choose an add-on, it usually specifies a file or you can specify it yourself. Do the latter, and you will have this essential add-on in your ubuntu magic machine.

I have compressed it and attached it, seeing as it is the only way to do so properly, so I am sorry for the inconvenience.

WARNING this is the data pak for 2003 but I hear it works with 2007 as well.... no guarantees

Strong fix. I believe the best OS is one that can seamlessly integrate proprietary while having all the benefits of OpenSource. I am also seeking membership in this community because I have worked with SAP and other important business systems and I see potential for Ubuntu to take over small business/corporation information systems to expand its funding and outperform the competition. The stability of Linux with the ability to insert and or design the proper software for keeping books is something I have done work on and I haven't had a dissatisfied client.

Interested in collaborators.

[email]dproestakes@gmail.com[/email]

---

### Post by linux fanatic on 2011-10-24
BTW.... Just to be clear, I made my toolpaks work by downloading this add on independently. Using the office disk to navigate to it didn't work for me, so that is why I just attached it. I also received it independently from a source online that freely distributed it.

---

### Post by gunksta on 2011-10-24
I don't know what license that file is distributed under, but I would be careful regarding where you post it. The site may (or may not) have permissions to host / distribute that file - but do you? Perhaps more importantly, does this right extend to the forum which is now hosting this file.

I'm not trying to call you our or act like a jerk. I think your willingness to follow up on this old thread and provide additional info is incredibly positive, I just don't want to see the forum getting in trouble over a file that the forum may not have permission to distribute.

Of course it is also entirely possible that this is totall OK. In that case, I think a quick link to the file's license / permissions might be a nice addition.

I suspect my evening may be spent playing around with Wine. Thanks.

---

