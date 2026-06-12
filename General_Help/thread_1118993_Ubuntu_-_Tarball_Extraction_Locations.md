---
title: "Ubuntu - Tarball Extraction Locations"
date: 2009-04-07
forum: General Help
---

### Post by Ticketoride on 2009-04-07
I download some Package, lets say OpenOffice 3.01, and I am being given the Option to either 'Save' or 'Extract" the compressed TAR Archive.

Do I just extract, or extract to some specified directory where all other packages are located? And where are they located?

Some Webpage states to run this ---> sudo dpkg -i <name of deb file>.deb

Does this Line need to be edited every time to reflect the Path where the Tarball was extracted such as:

sudo dpkg -i /Home/<SomeDirectory>/<name of deb file>.deb

Does one cd .. one's Way via the Terminal to the Directory where the Tarball was extracted first, and then enter the command?

There appears to be no standard Methodology for Installation, and every single Package I have been to trying install requires extensive Linux Forum Searches for specific Instructions.

Thx

---

### Post by maheshasolkar on 2009-04-07
When you download a compressed TAR Archive (.tar.gz,.tgz, etc files), you can open it in an Archive Manager - if you double-click on the archive, it should typically open in an Archive Manager. Archive Manager will show you what is inside the archive. You can then drag-and-drop the contents of the archive to a known directory (Desktop or such).

If there is a .deb file in the archive, you should be able to just double-click the .deb file and it will open in a package manager (dpkg). If you want to use the command line, you mention in the post.

---

### Post by woodenbrick on 2009-04-07
Very rarely should you have to install deb packages in this way.  You should be using synaptic (see System -> Administration).  If you wish you can run from the command line like so:
sudo apt-get install package-name

However if you have downloaded a package and want to install it with dpkg don't extract the .deb and you don't need to run cd either.

eg. sudo dpkg -i /path/to/deb/debfile.deb
Use the tab key for completion in case you didn't know about it already, it makes directory changing very quick.

Double clicking the .deb file should also run the gui installer.

---

### Post by coffeecat on 2009-04-07
> **Ticketoride said:**
> I download some Package, lets say OpenOffice 3.01

Was that a 'for instance', or did you really download OpenOffice 3.01? If the latter, go to Applications > Office. You might get a pleasant surprise.

> **Ticketoride said:**
> There appears to be no standard Methodology for Installation

Yes, there is. A previous poster has told you about Synaptic and the command line apt-get and now I've got another pleasant surprise for you. Go to Applications > Add/Remove. Pretty isn't it? It's only a tarted up Synaptic, but it's useful for newcomers to Ubuntu who don't know the (sometimes obscure) names of the various (and plentiful) software packages that are in the repositories.

---

### Post by Ticketoride on 2009-04-07
> **maheshasolkar said:**
> If there is a .deb file in the archive, you should be able to just double-click the .deb file and it will open in a package manager (dpkg). If you want to use the command line, you mention in the post.
Thnak you. That answers that. Just launch/execute the Puppy to install the Program/Package.

You mentioned ... 
> **maheshasolkar said:**
> If there is a .deb file
... does this apply only to *.deb Files or others too? And so which ones? What is/are the Rules for Double-Clicking what Files to run the install Process?
> **woodenbrick said:**
> Very rarely should you have to install deb packages in this way. You should be using synaptic (see System -> Administration). If you wish you can run from the command line like so: sudo apt-get install package-name
OpenOffice 3.01 is not available for Ubuntu 8.04 and does not download that Version via Synaptic by simply updating the Lists (Probably because it hasn't received Canonacial Blessings yet). I have to download it from the OpenOffice Site ... but where do I extract it to so Synaptic recognizes it as one of the Packages available for Installation?

Can Synaptic recognize it, and how do I go about making it recognize it?
> **woodenbrick said:**
> However if you have downloaded a package and want to install it with dpkg don't extract the .deb and you don't need to run cd either.

I extracted the *.deb out of the *.tar Archive
> **woodenbrick said:**
> Use the tab key for completion in case you didn't know about it already, it makes directory changing very quick.
Thanks for the Tip ...
> **woodenbrick said:**
> eg. sudo dpkg -i /path/to/deb/debfile.deb
Ok. So I can just edit the Line to reflect the Path. Cool.

---

### Post by coffeecat on 2009-04-07
> **Ticketoride said:**
> OpenOffice 3.01 is not available for Ubuntu 8.04 and does not download that Version via Synaptic

Two points:

You've got "Jaunty Jackalope testing' in your username pane. It was a reasonable assumption that that was the version you were using since you didn't mention 8.04 in your original post. (Jaunty comes with version 3.01.) If you want relevant help, I suggest you help yourself by providing relevant information in the first place.

You can install 3.01 via Synaptic if you enable the appropriate repository. A search of the forum will show you how.

---

### Post by Ticketoride on 2009-04-07
> **coffeecat said:**
> Was that a 'for instance', or did you really download OpenOffice 3.01? If the latter, go to Applications > Office. You might get a pleasant surprise.
I did. All went off without a Hitch using the Command Line. But I had to move the *.deb around many Times to various Directories before I got it to install using the Terminal. I am not quite sure how I did it in the End, but it was not Walk in the Park. I know I edited the "sudo" Line Path many Times before I finally was not greeted with a "File not found" Message.
> **coffeecat said:**
> A previous poster has told you about Synaptic and the command line apt-get and now I've got another pleasant surprise for you.
Then I must be missing some Information on "How-tos" somewhere.

How does the "apt-get" Command acquire a Package from a Website such as OpenOffice via a WebLink?

I had to click on the Link to download OO 3.01, and when done, the Archive Manager asked me where I wanted to extract or save the File.

How do I download and install OpenOffice 3.01 using the "apt-get" Command when its not in the Ubuntu Repository?

That means I have to download it from their Website, save/extract it somewhere, and then "execute" it. I have no clue what the "apt-get" Command has to do with any of that.
> **coffeecat said:**
> Go to Applications > Add/Remove. Pretty isn't it?
So where do I save the downloaded *.deb file to so Add/Remove can install it?
> **coffeecat said:**
> It's only a tarted up Synaptic, but it's useful for newcomers to Ubuntu who don't know the (sometimes obscure) names of the various (and plentiful) software packages that are in the repositories.
I have no Clue what most of the Repostory Packages are about. I know what Programs I want, some I do install via Add/Remove, but others are not in the Repository and I have to download them in *.tar Archive Formats from Websites.

Its when I have to download it where Problem comes in. So far I have extracted the Contents and run command line to install them, but it works sometimes, but mostly not.
> **coffeecat said:**
> You've got "Jaunty Jackalope testing' in your username pane. It was a reasonable assumption that that was the version you were using since you didn't mention 8.04 in your original post.
Sorry about the Confusion. 

1. I was using installing OpenOffice 3.01 as an Example in the OP, since I was looking for an Answer how to install archived (*.tar) Packages from Websites, and some sort of standard.

2. Ubuntu 8.04 has about 30 Minutes of Life left before it gets axed and I install 9.04 Beta.
> **coffeecat said:**
> If you want relevant help, I suggest you help yourself by providing relevant information in the first place.
The OP clearly states its an Example. I have no queries which are specific to 8.04 but a general Procedure for such Installations.
> **coffeecat said:**
> You can install 3.01 via Synaptic if you enable the appropriate repository.
What Key Search Words should I use to locate existing Threads on the Topic about that?

---

### Post by coffeecat on 2009-04-07
> **Ticketoride said:**
> So where do I save the downloaded *.deb file to so Add/Remove can install it?

OK, I can see where some of your confusion is coming from, so I've quoted just one comment. You can apply it to others.

So long as you have a good broadband connection, installing software is a breeze in Ubuntu. Synaptic (System > Administration) and Add/Remove are just GUI front-ends for apt-get. Whenever you click on 'Reload' in Synaptic or Software Update, the system will download metadata for all the applications available in the repositories that are enabled on your system. Selecting apps for installation will cause them to be automatically downloaded and installed by the package manager.

It's a revelation to newcomers used to Windows. "But it's so easy!" :shock:

And you don't pre-download debs to install with Add/Remove. It does it for you.

Once you've got the hang of installing software from the default repositories, ask and you'll be shown how to enable more (such as Medibuntu). Have fun! :)

**Edit:** you asked about installing OOo 3 via Synaptic, Have a look at post 29 in [this thread](http://ubuntuforums.org/showthread.php?t=946439&page=3). You'll need help adding those lines to your sources.list file though. Just post when you're ready and someone will walk you through it.

---

### Post by Ticketoride on 2009-04-07
> **coffeecat said:**
> So long as you have a good broadband connection, installing software is a breeze in Ubuntu. Synaptic (System > Administration) and Add/Remove are just GUI front-ends for apt-get. Whenever you click on 'Reload' in Synaptic or Software Update, the system will download metadata for all the applications available in the repositories that are enabled on your system. Selecting apps for installation will cause them to be automatically downloaded and installed by the package manager.
Understood. There are however Applications I would like to install which are not in the Repository and I have to download them from Websites. For Instance, as in the OP Example I cited earlier, OpenOffice 3.01 is not in their Repository even after "Reload".

So, if I want to install 3.01, I have to go to the OpenOffice Website, click on the Download Link. After download has been completed, the Archive Manager asks me what I would like to do with the downloaded File *.tar File.
> **coffeecat said:**
> And you don't pre-download debs to install with Add/Remove. It does it for you.
Ok. Considering I have already "reloaded" Synaptic or Software Update, and the Program I wish to install is not available, then I would assume the next Course of Action I undertake is to go to the Website which does have it available for download. I then download it. The next Thing I wanted to know is what is the standard Course of Action to install such Packages.
> **coffeecat said:**
> You'll need help adding those lines to your sources.list
Excellent. That answers that. Seems everything should come down by Sources.list. Should this information generally not be posted on Websites which have Linux Software for download? Seems one is always stuck for another Item to be added to the Sources.list and has to search around for the  Synaptic download Sources.

I ask this because for Windows one simply downloads an Executable and then runs it to install the Software. Seems to me the same Type of File downloading and some Sort of install Procedure should be viable for Linux.

Thx for all your Help.

---

### Post by mb_webguy on 2009-04-07
Add [this PPA]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") to your Software Sources (and don't forget to add the gpg key), and then install OOo3 through Add/Remove.

---

### Post by Ticketoride on 2009-04-07
> **mb_webguy said:**
> Add this PPA to your Software Sources (and don't forget to add the gpg key), and then install OOo3 through Add/Remove.
Thank you. A very valuable Link. I will look into that a little later today after I have installed 9.04.

Why would Websites have Linux Software download Links without indicating any Method of Installation?

If its all supposed to come from Repositories, then why don't Websites simply tell you what to enter into your Sources.list instead of having People download the File(s).

Likewise, sometimes several Files need to be downloaded in order to compile, ./configure, make and install the Software.

And that is what I would like to know. It would be kinda nice to have the Freedom to not be limited to Repositories and I can download whatever I want and install it. I was hoping there would be a standard Procedure for that.

I also recently tried to install Gimp 2.6.6 on Ubuntu 8.04 since that was in no Repository but needed to be compiled from 3 seperate Downloads. Halfway through the Instructions I got bogged down because of /root Issues & 'Permission Denied', which refused to lift irrespective of what I did with dozens of Advices from others under Consideration. Also, everything I download has a "Lock" above the Icon and the Files cannot be deleted. With better than 20GBs of undeletable downloaded Files cluttering my Desktop, I am forced to wipe out 8.04 and start anew, this Time killing off this "Permissions" Nonsense right off the Bat once and for all. Changing gdm.conf from "False" to "True" also receives these same "Permissions Denied" Messages.

If the Securities of Ubuntu are such that they impede me with "Denied Permissions" at every Stop which cannot be undone, I will have to turf Ubuntu for another Distro.

---

