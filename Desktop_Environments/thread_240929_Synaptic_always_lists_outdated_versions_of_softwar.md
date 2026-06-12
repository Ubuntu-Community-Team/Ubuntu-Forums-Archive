---
title: "Synaptic always lists outdated versions of software applications"
date: 2006-08-21
forum: Desktop Environments
---

### Post by harshad on 2006-08-21
Synaptic is a great and simple way to install software on Ubuntu. However it invariably lists versions that are at least 4 months old. 

I love to have the latest and greatest of software and that is getting quite difficult with Ubuntu. 

Any suggestions/fix? Or are there any download sites like download.com that have the latest software for Ubuntu? 

Very few applications provide .deb files. So installing directly also doesn't work in most cases.

---

### Post by ohgod on 2006-08-21
Are you talking about any specific application?

---

### Post by randell6564 on 2006-08-21
> **harshad said:**
> Synaptic is a great and simple way to install software on Ubuntu. However it invariably lists versions that are at least 4 months old. 

I love to have the latest and greatest of software and that is getting quite difficult with Ubuntu. 

Any suggestions/fix? Or are there any download sites like download.com that have the latest software for Ubuntu? 

Very few applications provide .deb files. So installing directly also doesn't work in most cases.

What are you wanting to install?  Where are you getting this info that is telling you that the software is old?  What are you comparing it to that you come to that conclusion?

---

### Post by Lord Illidan on 2006-08-21
Simple. Compile your own.

Google for what you want, then go to the project's home page, and download and compile the source.

You will need to download a bunch of dependencies though, but you can probably use the ones in the repositories, especially for devel.

If you have any other issues, post in the forums.

---

### Post by randell6564 on 2006-08-21
> **Lord Illidan said:**
> Simple. Compile your own.

Google for what you want, then go to the project's home page, and download and compile the source.

You will need to download a bunch of dependencies though, but you can probably use the ones in the repositories, especially for devel.

If you have any other issues, post in the forums.

Well.,I guess that would be some good advice IF harshad knows anything about what you are talking about!

Stating that it is "simple" is a bit cocky, dont you think?

Compiling from source actually, in my opinion Sucks to say the least! You gave a couple of reasons why!  Finding dependencies to a new linux user is ridiculous and, I believe is why some folks climb up onto rooftops and start shooting people!

---

### Post by Dubbayoo on 2006-08-21
Assuming that synaptic is updating the list of available software when you run it then what is there IS the latest and greatest. I think in most cases pkgs are updated within a month or so.

---

### Post by abelthorne on 2006-08-21
Most softwares in the official repositories are stable versions and are not updated until a new stable version is available.
In some cases, application updates are scheduled for next release of Ubuntu, even if it is stable enough.

Some Ubuntu users make their own updates of some softwares and maintain alternative repositories. This allows you to install and get updates to softwares quickly without having to compile your own or wait for the next release of Ubuntu.

---

### Post by harshad on 2006-08-22
1) Opera Browser, Java SE, HpLip printer drivers, bluefish editor and  OpenOffice are just some examples of old versions being listed on Synaptic. 

2) Compiling the programs I need is beyond my interest and capacity

3) Considering that there are thousands of software in Synaptic, is there some way in which we can help / inform the Synaptic people about new versions having been released?

4) As regards stable releases, Synaptic often does not have the latest stable releases for popular software that have releases every couple of months. 

thanks
harshad

---

### Post by mcduck on 2006-08-22
There is no need to inform 'synaptic people'(=ubuntu developers) that there are new versions available. They are trying to keep the current Ubuntu version stable and adding new software versions might break that and cause problems.

New Ubuntu versions are released every 6 months, and the stable version gets basicly no updates for other than security reasons. So you'll get your new software in next Ubuntu version, not before that.

If you want always-up-to-date packages instead of stability you could install Edgy (the development version of Ubuntu) or some other distro like Gentoo. Some software might also be available as backports but because of dependency troubles not everything can be made available that way.

---

### Post by aysiu on 2006-08-22
> **harshad said:**
> 1) Opera Browser, Java SE, HpLip printer drivers, bluefish editor and  OpenOffice are just some examples of old versions being listed on Synaptic. Opera is version 9, just as it is on the Opera website. Is there something I'm missing?

Frankly, I don't really care whether I have OpenOffice 2.0.2 or 2.0.3. Here's the changelog. Does any of this matter to people that they can't wait six months for it? ```
Feature title  	TaskId  	Spec. title  	Spec. abstract  	Dev. owner  	Spec. link  	Component
Malayalam (ml_IN) locale data 	i59935 	  	feature-info:
Added Malayalam (ml_IN) locale data, which makes it a fully supported locale. 	  	
	L10N
Akan_Ghana (ak_GH) locale data 	i60109 	  	feature-info:
Added Akan_Ghana (ak_GH) locale data, which makes it a fully supported locale. 	  	
	L10N
Latin_Vatican (la_VA) locale data 	i64838 	  	feature-info:
Added Latin_Vatican (la_VA) locale data, which makes it a fully supported locale. 	  	
	L10N
Single Cell Mode for range selection 	i40174 	  	feature-info:
The parameter sequence com.sun.star.sheet.RangeSelectionArguments for the startRangeSelection call of com.sun.star.sheet.XRangeSelection can now contain an optional boolean property "SingleCellMode". If this property is given and TRUE, only a single cell will be given as the result of the range selection. Thanks to Kohei Yoshida for providing the patch. 	  	
	api
text/csv files can be read with UTF-8 encoding 	i44354 	  	feature-info:
With the integration of CWS dba203b, text/csv databases can now make use of the UTF-8 encoding. That is, if you have a "comma separated text" file you want Base to read, and this file is encoded in UTF-8, then you can now choose this encoding in Edit / Database / Properties ... / Character Set. 	  	
	dba
"Copy Table" auto pilot "Append Data" instead of "Attach Data" 	i47324 	  	feature-info:
Minor change: In the "Copy Table" auto pilot, on the first page, the radio button "Attach Data" has been renamed to "Append Data", which better reflects what is going to happen. 	  	
	dba
Support MS file format for "Send Document as E-Mail" 	i46895 	Send Document as E-mail 	The feature Send Document as E-mail is often used by customers who need to work with Microsoft document formats. Currently – in OpenOffice.org 2.0.2 – a user has to set the default file format with the Tools – Options dialog to the Microsoft document formats to easily use Send Document as E-mail. This is first not very intuitive, but there is also a second problem. There are many customers who want to use the OpenDocument format by default, but from time to time have to send documents with the Microsoft document format. They have to save a document in Microsoft document format before they can use Send Document as E-mail. The following enhancement wants to help people who need to work with these two file formats (Microsoft document and OpenDocument format). 	[email]carsten.driesner@sun.com[/email] 	speclink 	framework
Changed close behavior and new function for context sensitive toolbar 	i50428 		Toolbars in OpenOffice.org are completely renewed. They have further on a context sensitive behavior, but without the toolbar toggle known from OpenOffice.org 1.1 or earlier. New is also that each OpenOffice.org program module can have its own toolbar configuration. The OpenOffice.org 2.0 toolbars provide a lot of usability enhancements which allow an easier customization of the toolbars. 	[email]carsten.driesner@sun.com[/email] 	speclink 	framework
non-pro: OSL assertions now appearing the same way as TOOLS-assertions 	i52747 	  	feature-info:
For quite some time now, OOo has two different diagnostics systems: OSL-based and TOOLS-based assertions. It's up to the developer of some piece of code which ones s/he uses. Failed TOOLS assertions usually are reported in a modal message box, but can be re-routed to other channels in the "VCL Debug Options" dialog (opened by pressing Ctrl-Alt-Shift-D). This dialog also offers some more options how to handle those assertions, for instance filtering. Failed OSL assertions are reported in a modal message box on Windows, and on the console on Linux. They cannot be re-routed or filtered at all, only globally disabled. Once the CWS gslpatches07 is integrated, OSL assertions can be captured by the TOOLS-based system, too. That is, OSL assertions then behave exactly the same way as TOOLS-based assertions. This behaviour can be switched off in the VCL Debug Options dialog, which contains a new check box labeled "Reroute osl debug messages", and is ON by default. All of the above of course only applies to non-product builds of OpenOffice.org. 	  	
	framework
non-pro: dbgsv.ini now human-readable 	i52821 	  	feature-info:
The "dbgsv.ini" file, which stores the debugging options of non-product builds (i.e. the settings made in the "VCL Debug Options" dialog), has formerly been stored in some binary format (basically, a memory dump of some internal structures). With the integration of CWS gslpatches07, this file is a human-readable INI file. 	  	
	framework
Registry .xcu format supports oor:op="fuse" 	i63706 	  	feature-info:
The registry .xcu format now supports the update operation oor:op="fuse", see for details. This is especially important for Jobs.xcu particles, see . 	  	
	framework
Corrected help id for xslt filter dialog basic tab page 	i63719 	XML Filter Configuration 	
	[email]philipp.lohmann@sun.com[/email] 	speclink 	framework
Library Export in Basic IDE 	i64017 		Hint: In this text only “OpenOffice.org“ is used as product name, but everything also applies to StarOffice. 	[email]andreas.bregas@sun.com[/email] 	speclink 	framework
Online update 	i64103 		Currently the user has to open manually the appropriate webpage which offers patches and updates for StarOffice/OpenOffice.org. Then he has to search for the needed update and activate the download also manually. The first step for accessing the appropriate patch or update should be eased by implementing the possibility to check for them from within StarOffice/OpenOffice.org. The user starts the online update manually from the menu and the following check for possible updates happenes automatically. This includes checking which update currently exists on the client and if there is a newer update available on the server. If a newer update is available, the user get forwarded to the webpage to initiate the next steps. 	[email]carsten.driesner@sun.com[/email] 	speclink 	framework
Easy to use complex toolbar controls for add-ons 	i64501 			[email]carsten.driesner@sun.com[/email] 	speclink 	framework
Import/export of custom document variables from/to MS formats 	i64516 	  	feature-info:
Custom document variables are now imported from and exported to Microsoft file formats (Word, Excel, PowerPoint). Custom document variables can be inserted in Microsoft Office applications via File -> Properties -> Custom. On import these variables are stored in the DocumentInfo property container at the document. They can be received for example in OOo Basic with ThisComponent.DocumentInfo.getPropertyValue( "custom-name" ) All property types available in MS Office are supported: String Number (signed 32-bit integer) Boolean DateTime Export to MS file formats works as well. 	  	
	framework
Additional features for PDF export 	i61139 	PDF Export Dialog 		[email]philipp.lohmann@sun.com[/email] 	speclink 	gsl
Controlling Slide Shows 	i54381 		
	[email]christian.lippka@sun.com[/email] 	speclink 	presentation
TestTool: new command IsProduct() as boolean 	i50125 	  	feature-info:
Provide command to get the build type of OOo. To be able to distinguish a 'normal' OOo build from a 'debug' or 'nonpro' build this command is introduced; Currently exist only ugly hacks, to get this information: - compare the filesize of a library - look in tools->options for special page To speed up the start up of a test this new command will be used. May get integrated around SRC680m165. The function is implemented in the TestTool application and needs a new sts-library on the OOo side. 	  	
	qa
testtool: command findObject ( string ) as object 	i54137 	  	feature-info:
Enhance Object handling to find objects by name and allow object ssignments As example: dim xx as object xx = findObject("FormWizard") print xx.id, xx.name if xx.exists() then print "exists" May get integrated around SRC680m165. The function is implemented in the TestTool application. 	  	
	qa
Page Preview can be closed with Escape key 	i46976 	  	feature-info:
The Page preview of the Spreadsheet application can be closed using the Esc-key. 	  	
	sc
CSV export data as displayed 	i4925 	Saving Cell Content as Displayed in Spreadsheet to CSV 		[email]eike.rathke@sun.com[/email] 	speclink 	sc
Naming of drawing objects in Calc 	i51351 		Single drawing objects and text boxes, contrary to grouped drawing objects, could not be named in Writer and Calc. It is an accessibility requirement to be able to do so. 	[email]niklas.nebel@sun.com[/email] 	speclink 	sc
idlc: no unsinged types as type arguments of instantiated polymorphic struct types 	i62339 	  	feature-info:
Until now, only unsigned integer types (i.e., UNSIGNED SHORT, UNSIGNED LONG, and UNSIGNED HYPER) were forbidden as type argumetns of instantiated polymorphic struct types in UNO (and idlc only generated errors for those cases). It was an oversight to not also forbid any unsigned types (i.e., also any sequence types that have unsigned component types). This has been fixed now in , and idlc has been changed to also generate errors in the previously missing cases. 	  	
	udk
Critical paths from Tools - Options - OOo - Paths removed 	internal 	Options > OpenOffice.org > Paths 	Several paths are critical to OpenOffice.org. If a user is not absolutely sure what she does in Options-Paths then OOo can refuse to launch the next time. Therefore, all but 5 paths are removed from the Options panel. The experienced user can still change the other paths by editing the configuration file. 	[email]hans-peter.burow@sun.com[/email] 	speclink 	ui
new shortcut ALT+F11 opens dialog for editing macros 	i29138 		new shortcut ALT+F11 opens dialog for editing macros 	[email]andreas.schluens@sun.com[/email] 	speclink 	ui
Removed Tools->Options->View: restore "Editing view" 	i53104 		OpenOffice.org 2.0.3 supports a hardware acceleration for rendering of presentations in Impress. An additional component is needed to enable the platform specific acceleration. Furthermore, graphic card drivers are 3rd-party products, which OpenOffice.org does not have any influence on. Additionally, there is a potential for bugs in those drivers, which can be unveiled by using OpenOffice.org. Since such problems can make OpenOffice.org presentations potentially unusable, we introduce an option which allows the user to disable the hardware acceleration support. 	[email]thorsten.behrens@sun.com[/email] 	speclink 	ui
Text of column header of font replacement changed 	i60897 	  	feature-info:
The text of the second column header of the font replacement options table has changed from "Screen" to "Screen only" (Geman: "Bildschirm" -> "Nur Bildschirm". 	  	
	ui
Cleanup in menubar.xml's 	i64286 	  	feature-info:
I have removed all menu:helpid's and menu:label's attributes from all recent menubar.xml's in 'menucleanup' child workspace - they are obsolete and unnecessary. This task should affect no functionality, these attributes are not used. 	  	
	ui
crash recovery restarts office immediatly 	i64599 	OpenOffice.org Error Reporter UI Specification 	The OpenOffice.org Error Reporting Tool and the document recovery features are combined into one work flow. When OpenOffice.org crashes the documents will be saved and users get informed abut the upcoming recovery process, followed by sending out an error report. 	[email]andreas.schluens@sun.com[/email] 	speclink 	ui
TestTool: Path selection dialog available for generic settings 	i63675 	  	feature-info:
In the VCL TestTool application on the tab page: Tools -> Settings -> Generic You get an additional button 'Path', above the button 'New' in the section 'Settings', if the feature is enabled for an 'Area' in the configuration file of the TestTool (.testtoolrc / testtool.ini) You have to set the line 'Type=Path' manually by editing the configuration file. example: [OOoProgramDir] Type=Path Current=. Currently this feature is only used for the entry [OOoProgramDir]. If you start the TestTool for the first time, and you don't have already a configuration file in your home directory, then you get the entry [OOoProgramDir] by default. 	  	
	util
Compatibility option: Keep-with-next attribute for table rows 	internal 	  	feature-info:
A new (non-UI) compatibility option "TableRowKeep" has been added to Writer documents. If this option is enabled, a table row can be forced to keep together with the next row by setting the keep-with-next attribute to the first paragraph within the first cell of this row. If this row is the last row of a table, the last row tries to keep together with the next content behind the table. This compatibility option is disabled per default and enabled during ww8/rtf import. 	  	
	word processing
German string "Extras - Wortanzahl" has been changed 	internal 	  	feature-info:
The German string "Extras - Wortanzahl" has been changed to "Extras - Wörter zählen". 	  	
	word processing
Page Preview can be closed with Escape key 	i35777 	  	feature-info:
The Page preview of the Writer application can be closed using the Esc-key. 	  	
	word processing
Compatibility option: Do not consider blanks and tabs for line height calculation 	internal 	  	feature-info:
A new (non-UI) compatibility option "IgnoreTabsAndBlanksForLineCalculation" has been added to Writer documents. If this option is enabled, the sizes of tab stop portions and blanks-only portions do not contribute to the line height calculation. This compatibility option is disabled per default and enabled during ww8/rtf import. 	  	
	word processing
Naming of drawing objects in Writer 	i51726 		Single drawing objects and text boxes, contrary to grouped drawing objects, could not be named in Writer and Calc. It is an accessibility requirement to be able to do so. 	[email]Oliver-Rainer.Wittmann@Sun.COM[/email] 	speclink 	word processing
New Default Table Formatting Behavior 	i60422 	New Default Table Formatting Behavior 	Predefined character formatting inside tables is unwanted by the user as we have learned in OOo 2.0 usability studies. Furthermore the formatting, used in the paragraph were the table has been inserted, is expected to be used in the table as well. 	[email]frank.meies@sun.com[/email] 	speclink 	word processing
```

---

### Post by Major_Stitch on 2006-08-22
I think the preoblem is not having enabled Backports repositories. Ubuntu doesn't have updates (only security fixes) for 6 months! If you enable backports repositories than you have access to updated programs like Firefox,Opera, etc.
HowTo enable Backports: [UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")

---

### Post by aysiu on 2006-08-22
I think the problem is people just being too anxious about having the cutting edge version of an application when the next-oldest version would suit them fine for six months.

Personally, I like having self-updating central repositories for all my software and having those repositories have new software every six months... as opposed to what I used to do in Windows--download manually and install manually newer versions of every single application I had.

---

### Post by Major_Stitch on 2006-08-22
> **aysiu said:**
> I think the problem is people just being too anxious about having the cutting edge version of an application when the next-oldest version would suit them fine for six months.

It really is somewhat spoiled, but people are new to that kind of system. I found it hard when I installed 4.10, but on 6.06 it doesn't bother me. People will get used to it, or ditch it. It's something you love or hate.

---

### Post by harshad on 2006-08-22
I appreciate the great work put into Ubuntu and Synaptic. 

Its just that at times when your printer doesn't work as expected and there's a new version of the drivers available, you hope that you could install the latest version and get your printer working properly.

For the majorty of users, i guess updates every 6 months is fine. However I would think Ubuntu should have more frequent updates for popular apps like OpenOffice, Java SE, HpLip, etc.

Can't there be a special vendor program, to encourage vendors to contribute to Ubuntu and update Synaptic's version to the latest version?

---

### Post by aysiu on 2006-08-22
There are backports. I guess it's just a matter of getting more people on board to actually backport applications and put them in the repositories.

---

### Post by rejser on 2006-08-22
Well mostly when there is a new version of a software that has changed anything major it is available quite soon by someone on the forum (howto department usually tells when it is).
Otherwise it's quite good to run a stable version.
You could turn to the devel-version which is more cutting edge

---

### Post by Lord Illidan on 2006-08-22
> 
Well.,I guess that would be some good advice IF harshad knows anything about what you are talking about!

Stating that it is "simple" is a bit cocky, dont you think?

Compiling from source actually, in my opinion Sucks to say the least! You gave a couple of reasons why! Finding dependencies to a new linux user is ridiculous and, I believe is why some folks climb up onto rooftops and start shooting people!

Nothing cocky about it, sorry.
And no, it doesn't suck.

If you think that ```
./configure;sudo make;sudo make install
``` is hard, then yes, perhaps you should use apt-get.

Otherwise it is a very simple affair.
Just run ./configure in a terminal, after you unzip the folder containing the application. ./configure will then examine your system for the necessary development packages.

It will halt if it doesn't find the necessary package. Then you can fire up synaptic and search for the necessary -devel or -lib package.

Thus, if it needs, say, libSDL_net or whatever, I just have to download it from Synaptic, then I can continue.
Rerun ./configure, then when it is ready, run sudo make; sudo make install.

Also, you are discounting the probability that an app may come in a binary form. All one needs to do is unzip the tar.gz folder that it comes in, and run the app directly from the folder.

So you might need to learn something about compiling...is it so hard to do so?

---

### Post by mssever on 2006-08-22
> **Lord Illidan said:**
> If you think that ```
./configure;sudo make;sudo make install
``` is hard, then yes, perhaps you should use apt-get.
I prefer to use ```
./configure && make && sudo make install
``` Note the double ampersands. That way, if there are errors during any step, the command will stop. So if configure failed, your machine won't try to run make. Note also the missing sudo. You don't need to be root to compile.

> Otherwise it is a very simple affair.
Just run ./configure in a terminal, after you unzip the folder containing the application. ./configure will then examine your system for the necessary development packages. The main reason that I no longer compile if I can help it is that compiling using the normal route doesn't result in .deb packages that can be managed in Synaptic (or apt-get). I like to maintain a clean system. However, I've lately used pbuilder ([HOWTO here]("http://www.ubuntuforums.org/showthread.php?t=206382")) and the Debian unstable source repository to compile .deb packages with newer versions than are in the Ubuntu repos. Also, pbuilder automatically takes care of dependencies.

To enable the Debian unstable source repo, add the following to /etc/apt/sources.list (using a US mirror):```
# Debian sources
deb-src http://http.us.debian.org/debian unstable main

``` Then run sudo apt-get update.
> Also, you are discounting the probability that an app may come in a binary form. All one needs to do is unzip the tar.gz folder that it comes in, and run the app directly from the folder. 
I don't like to install binary versions of programs from outside the repos for the same reason that I don't like to compile. My old Red Hat system became quite bloated after awhile--my chief reason for switching to a Debian-based distro.

---

### Post by Gustav on 2006-08-22
> **mssever said:**
> The main reason that I no longer compile if I can help it is that compiling using the normal route doesn't result in .deb packages that can be managed in Synaptic (or apt-get). I like to maintain a clean system. However, I've lately used pbuilder ([HOWTO here]("http://www.ubuntuforums.org/showthread.php?t=206382")) and the Debian unstable source repository to compile .deb packages with newer versions than are in the Ubuntu repos. Also, pbuilder automatically takes care of dependencies.
You could also use 'sudo checkinstall' instead of 'sudo make install'. That way a .deb package is created and installed and can easely be removed via synaptic.

---

### Post by Lord Illidan on 2006-08-22
I dunno why, but just make doesn't work.. I tneeds to be sudoed..perhaps something wrong I'm doing?

---

### Post by randell6564 on 2006-08-22
Also, I'm quite sure that new versions of java are available just by enabling your multiverse repo's, and doing a 'sudo apt-get update'

---

### Post by mssever on 2006-08-22
> **Lord Illidan said:**
> I dunno why, but just make doesn't work.. I tneeds to be sudoed..perhaps something wrong I'm doing?

Not sure...I must confess that most of my compiling experience is on Red Hat. Perhaps Ubuntu restricts access to make? Or maybe you are doig something wrong...

---

### Post by glennric on 2006-08-22
> **randell6564 said:**
> Also, I'm quite sure that new versions of java are available just by enabling your multiverse repo's, and doing a 'sudo apt-get update'

Actually, the version of Sun's java in the repositories is two behind the latest release.

---

### Post by randell6564 on 2006-08-22
> **glennric said:**
> Actually, the version of Sun's java in the repositories is two behind the latest release.


Which java are you refering to?

The one BEFORE enabling multiverse or after?

---

### Post by asplode on 2006-08-23
I've had excellent luck with necessary development packages in Ubuntu.  Not being cocky, but it couldn't really be simpler.

```
sudo apt-get build-dep (application name)
```
so for banshee
```
sudo apt-get build-dep banshee
```
and blammo kerpresto.  All necessary development packages and dependencies are installed.  If you think that's hard, play around with RPMs for a bit, and then you really *will* run to a rooftop with a gun.

---

### Post by randell6564 on 2006-08-23
> **asplode said:**
> I've had excellent luck with necessary development packages in Ubuntu.  Not being cocky, but it couldn't really be simpler.

```
sudo apt-get build-dep (application name)
```
so for banshee
```
sudo apt-get build-dep banshee
```
and blammo kerpresto.  All necessary development packages and dependencies are installed.  If you think that's hard, play around with RPMs for a bit, and then you really *will* run to a rooftop with a gun.

Yes, but installing something that you can get from synaptic is a given. There is really no need to have to deal with Dep's, synaptic does it for you.

I'm wondering.,if it is so simple why do we even HAVE a package manager?

Thank you though, for the tip!  "sudo build-dep" will be going into my personal ManPages folder!

---

### Post by mssever on 2006-08-23
> **randell6564 said:**
> Yes, but installing something that you can get from synaptic is a given. There is really no need to have to deal with Dep's, synaptic does it for you.

I'm wondering.,if it is so simple why do we even HAVE a package manager?
Synaptic is merely a graphical front-end for apt-get and its cousins. If you've ever used a distribution that doesn't use APT (such as Red Hat), you'll realize why we have APT. Installing software is simple *because* of APT. If there is no package manager, then managing software means compiling and/or installing software using whatever means the author intended. Then, upgrading/uninstalling software becomes a real nuisance, and after time you wind up with a lot of old software that you don't need anymore. Not only that, but when you go to upgrade, you find that you need to upgrade something else first. So, you go to upgrade that, and you end up having to upgrade yet another program, and so on.

The beauty of APT is that it solves all these problems so that installing and managing software becomes simple.

---

### Post by randell6564 on 2006-08-23
> **mssever said:**
>  Then, upgrading/uninstalling software becomes a real nuisance, and after time you wind up with a lot of old software that you don't need anymore. Not only that, but when you go to upgrade, you find that you need to upgrade something else first. So, you go to upgrade that, and you end up having to upgrade yet another program, and so on.

The beauty of APT is that it solves all these problems so that installing and managing software becomes simple.

EXACTLY!!  THAT is what I meant when I replied to asplode's comment of "but it really couldn't be simpler"

---

### Post by randell6564 on 2006-08-23
> **mssever said:**
>  Then, upgrading/uninstalling software becomes a real nuisance, and after time you wind up with a lot of old software that you don't need anymore. Not only that, but when you go to upgrade, you find that you need to upgrade something else first. So, you go to upgrade that, and you end up having to upgrade yet another program, and so on.

The beauty of APT is that it solves all these problems so that installing and managing software becomes simple.

EXACTLY!!  THAT is what I meant when I replied to asplode's comment of "but it really couldn't be simpler"

BTW.,This forum is really beginning to SUCK!  Not you guy's, but Canonical!

It's taking me over a Fricken minute to post! Then I usually get a time out, and have to rewrite my response!  Come on guy's, get with the program!

---

### Post by glennric on 2006-08-24
> **randell6564 said:**
> Which java are you refering to?

The one BEFORE enabling multiverse or after?

I am referring to the version in the repositories after enabling multiverse.  It is version 1.5.0-06.  The latest version of sun java available is 1.5.0-08.  Visit [http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp")
to see that the latest version is not installed.

---

### Post by ThirdWorld on 2006-08-25
> **Lord Illidan said:**
> Simple. Compile your own.

Google for what you want, then go to the project's home page, and download and compile the source.

You will need to download a bunch of dependencies though, but you can probably use the ones in the repositories, especially for devel.

If you have any other issues, post in the forums.

 oh my dear lords....   :rolleyes:

---

### Post by ThirdWorld on 2006-08-25
sometimes i wonder if some of this guys belong to a diferent species... :mrgreen:

---

### Post by Animortis on 2006-08-29
> **ThirdWorld said:**
> sometimes i wonder if some of this guys belong to a diferent species... :mrgreen:

You're telling me. Does he honestly think a distro can answer a desktop user with "Compile your own" after that distro has been sold for a large market?

I'm sorry, but it's clear to me Ubuntu developers aren't listening to their users. Users ask for fresher software for more features, improvements and functionality, and developers happily say older versions are more than sufficient. Have they ever tried to do a page layout with an old Scribus version? Or an SVG drawing with an old Inkscape version?

It's not the company's job to tell users what they want, it's the user's job to tell the company what they want. I find the answer of "Compile your own" highly unprofessional. Get those billboards down, please.

I'm going to give Ubuntu another week. If I can't find answers for this old, junky software I'm giving up on it.

---

### Post by mssever on 2006-08-29
> **Animortis said:**
> You're telling me. Does he honestly think a distro can answer a desktop user with "Compile your own" after that distro has been sold for a large market?

I'm sorry, but it's clear to me Ubuntu developers aren't listening to their users. Users ask for fresher software for more features, improvements and functionality, and developers happily say older versions are more than sufficient. Have they ever tried to do a page layout with an old Scribus version? Or an SVG drawing with an old Inkscape version?

It's not the company's job to tell users what they want, it's the user's job to tell the company what they want. I find the answer of "Compile your own" highly unprofessional. Get those billboards down, please.

I'm going to give Ubuntu another week. If I can't find answers for this old, junky software I'm giving up on it.
The latest stable version of Inkscape is 0.44. The version installed on my machine is 0.43. That's only only version behind. And it's worth noting that given the rapid development (and version number changes) of beta software such as Inkscape, it's difficult to keep the latest version in the repos, while making sure that's it's been adequately tested. Remember, Ubuntu's release schedule is to release new versions once every six months and keep everything the same in between (except for security updates). When I as using Windows, I rarely used software that was merely six months old!

---

### Post by tuxcantfly on 2006-08-30
if you ask me, what we really need is something like gentoo's portage and ebuild systems. along with the stable apt-get method, we should, instead of apt-build, have one for the cutting edge people; just like gentoo, a script that automatically gets the latest from cvs and builds it. it'll be completely up to date, low maintainence (just write the script and you're done, cvs will update itself for you), and will satisfy those who whine on that version x of software y isn't in the repos. just stuff it under some "highly experimental" section of synaptic, warn the newbs, and let those who desperately need new versions try it out.

---

### Post by tuxcantfly on 2006-08-30
in fact, since ebuilds are just scripts, we can modify portage to generate deb packages and install them, instead of installing them directly. think of it: it'll let all ubuntu users install any ebuild effortlessly, withought having to modify them! given how big gentoo's ebuild repos are (way bigger and up to date than ubuntu's apt, I heard), this could be a good addition to ubuntu. in fact, with another modification, we could even use apt's interfaces for this ebuild-deb thing. imagine: user wants cutting-edge code, he enables the gentoo repos, and gets the ebuilds, cvs checkout, builds, creates a deb, and installs it, all within Synaptic!

---

### Post by mssever on 2006-08-30
Sounds great to me! I'd use such a system.

---

### Post by nrwilk on 2006-08-30
> **glennric said:**
> I am referring to the version in the repositories after enabling multiverse.  It is version 1.5.0-06.  The latest version of sun java available is 1.5.0-08.  Visit [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
to see that the latest version is not installed.

Going to the exact link you gave me I got this:
> **We detected your Java environment as follows**;
[IMG]http://www.java.com/im/a.gif[/IMG]Java Runtime Vendor: Sun Microsystems Inc.
  Java Runtime Version: 1.5.0_06
  [IMG]http://www.java.com/im/a.gif[/IMG]  
   CONGRATULATIONS, you have the Latest version of Java! 

If I go to download the file from Sun's website, I get a file called jre-1_5_0_06-linux-i586.bin.  That's 1.5.0_06.

Java 1.5.0_08 only comes when you download and install java's jdk version 1.5.0_08, which many will not do.  So, 1.5.0_06 is the latest for most casual users.  Unless you're developing, there's no difference.

Screen shot attached:

---

### Post by glennric on 2006-09-01
> **nrwilk said:**
> Going to the exact link you gave me I got this:
 

If I go to download the file from Sun's website, I get a file called jre-1_5_0_06-linux-i586.bin.  That's 1.5.0_06.

Java 1.5.0_08 only comes when you download and install java's jdk version 1.5.0_08, which many will not do.  So, 1.5.0_06 is the latest for most casual users.  Unless you're developing, there's no difference.

Screen shot attached:

When I go to this site now it tells me that I have the latest version installed as well.  I do have the jdk version installed.  However, regardless of what that site is telling us, if you go to [http://java.sun.com/javase/downloads/index.jsp]("http://java.sun.com/javase/downloads/index.jsp"), you can see that the java runtime environment update 8 is available.

---

### Post by nrwilk on 2006-09-01
> **glennric said:**
> When I go to this site now it tells me that I have the latest version installed as well.  I do have the jdk version installed.  However, regardless of what that site is telling us, if you go to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp), you can see that the java runtime environment update 8 is available.

Right.  I guess my point was that people aren't missing anything if they're running update 6 rather than 8.  The java site still identifies it as up-to-date.

---

### Post by etherstream on 2006-09-01
Yeah, I tend to agree with that point.

---

### Post by johnbl on 2006-09-29
Whilst you guys are discussing versions - how does a dumb a as I go about seeing which versions of software are installed anyway?
Is there a definative log somewhere or a command line trick to use in terminal?

For instance;

Currently have a cd payer that wont and looks like from forum posts I am far from alone. An update has broken something but when people start in about whatever ver x.x.x being a problem and IF you have it to reinstall X.X.-x it leaves the point begging. Just how to find out that version number across all the app files!

Probably a stuid Q but I'd still really like to know......... <sigh>:rolleyes: 

Chhers on and all

---

