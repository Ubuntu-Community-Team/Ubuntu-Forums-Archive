---
title: "MLdonkey, how to set it up?"
date: 2005-11-17
forum: Desktop Environments
---

### Post by sickdude on 2005-11-17
as the topic name says, how do i set up a mldonkey server?

is there a nice how to or is there somebody that does this often?

any help would rock

thnx

---

### Post by sudokubuntu on 2005-12-09
found this [http://talk.trekweb.com/~jasonb/articles/mldonkey_linux.shtml](http://talk.trekweb.com/~jasonb/articles/mldonkey_linux.shtml)

trying to set it up too, just taking it step by step:confused:

:edit:

the things I have done is to get the mldonkey-server and kmldonkey GUI from the repositories.
Then I typed (I think) kmldonkey in the terminal to start that up.
It'll ask you to assingn it to the mlnet executable, on my machine it was in usr/bin.
then I had to start mlnet with "sudo mlnet" to make kmldonkey connect to it.

Now I'm configuring the whole thing.
That's how far I've come.

If anyone knows how to make mlnet start up automatically (without me typing "sudo mlnet" to get it going) any help would be appreciated. Or how to gain ownership over the file.

YO

---

### Post by tom-ubuntu on 2005-12-10
just do a "sudo apt-get install mldonkey-server". The package will be installed and it will ask you, if you would like to start is as a deamon. Say "yes" here. Then it should work.

I just set it up myself. Got just one problem: The package is too old; I am getting this when I try to connect to a server: 
*ERROR : Your edonkey client is too old, please update it*

Are there any up to date packages around I can use?

---

### Post by sudokubuntu on 2005-12-10
I'm having troubles with my ubuntu install right now, so I'll have to deal with that.
But if you check out kmldonkey's website (kde's GUI) you'll find some links to the latest versions.

Or MLdonkey world or something.

I wont set it up now, but I'll try again later, then I'll come back here and look for a solution  :)

---

### Post by AudioBookDiety on 2005-12-14
The super easy MLDonkey setup method.
  There is no real need to actually have MLDonkey installed by apt/rpm/smart/etc. I have never done it that way and never had any kind of dependency problems.

 Step 1.  Download the latest MLDonkey core...you will find it here;              [URL="http://download.berlios.de/pub/mldonkey/spiralvoice/"][COLOR="Blue"]Download[/COLOR]
[/URL]
 Step 2. Extract what you just downloaded into your home directory, or some other directory which you own. { Large free space recomended }

 Step 3. [Optional] Rename the extracted folder something simpler like mldonkey or ml or something. Instead of some insanely long name like example-2.0.1.3.1.-401-i-love-to-type-supurflous-garbage.

 Step 4. open a terminal and type the full path of wherever the mldonkey folder is...IE /share/mldonky  then add /mlnet  so you would have /share/mldonkey/mlnet and hit enter. MLDonkey is now running.

 Step 5. You have many options here. I'll give two easy ones.
   5a. Open a web browser and type in 127.0.0.1:4080 as the address. It will be obviouss from there. [assuming 4080 is still the web interface default]
   5b. Run KMLdonkey {or install and run}. If it is the first time you should be in the wizard, if you have run it before you will find the wizard under settings 'KMLDonkey setup wizard' or with focus on KMLDonkey hold shift and hit K. Follow the wizard and enter /share/mldonkey as your working directory, and /share/mldonkey/mlnet as your core. You should be all set. [ most often when running KMLDonkey under Gnome it will not automatically start the core. But no worries just start it from the command line/run/or create launcher]
  5c. run or install any number of other GUIs for MLDonkey.

 REPLACE ALL DIRECTORIES WITH THE ONES YOU USE

 This should work for most people. I have not yet done this in ubuntu but I have done it this way under SUSE, Mandriva, Debian, Yoper, Mepis, and others. I think I remeber it working everytime.

---

### Post by sudokubuntu on 2005-12-15
THANKS for the nicely written tutorial :D

Now, what I'm thinking, is to try to make it resume the downloads that I already have running in aMule and Azureus.
Maybe just put them in the MLdonkey folder and open the torrents?
It's not a big deal though. I'll just finish them.
And I'll figure it out.
Thanks again.

---

### Post by AudioBookDiety on 2005-12-17
Not posotive on all that may need to be done to add part files. One hint though, no matter where you put the core [mlnet] there will be a hiiden file in your haome folder /home/username/.mldonkey .

 Also I had forgot to mention. The reason i had not tried to use MLDonkey in Kubuntu is that I have switch to Amule, which i find is a much much bettter client for ed2k.
 You can install it if you use that easy Ubuntu thing they built,{just search the forums for it..if like me you use Kubuntu they have one for it as well but it is buggy} or just add the Penguin Liberation Front repositiries yourself

## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free 
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free 

## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free 
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free

---

### Post by sudokubuntu on 2005-12-18
[QUOTE=AudioBookDiety]Not posotive on all that may need to be done to add part files. One hint though, no matter where you put the core [mlnet] there will be a hiiden file in your haome folder /home/username/.mldonkey .

 Also I had forgot to mention. The reason i had not tried to use MLDonkey in Kubuntu is that I have switch to Amule, which i find is a much much bettter client for ed2k.
 You can install it if you use that easy Ubuntu thing they built,{just search the forums for it..if like me you use Kubuntu they have one for it as well but it is buggy} or just add the Penguin Liberation Front repositiries yourself

## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free 
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free 

## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free 
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free[/QUOTE]

Hey thanks.
I discovered those hidden folders in the home folder.
Think it was a bit difficult to set up the way I wanted it, so I'll use aMule for a while too.
I have a pretty new one too I think, found it from some thread here, some cool guy making his own aMule dep-packages.
Thanks for the help though.

---

### Post by cvmostert on 2006-01-31
> **AudioBookDiety]The super easy MLDonkey setup method.
  There is no real need to actually have MLDonkey installed by apt/rpm/smart/etc. I have never done it that way and never had any kind of dependency problems.

 Step 1.  Download the latest MLDonkey core...you will find it here said:**
> [COLOR="Blue"]Download[/COLOR]
[/URL]
 Step 2. Extract what you just downloaded into your home directory, or some other directory which you own. { Large free space recomended }

 Step 3. [Optional] Rename the extracted folder something simpler like mldonkey or ml or something. Instead of some insanely long name like example-2.0.1.3.1.-401-i-love-to-type-supurflous-garbage.

 Step 4. open a terminal and type the full path of wherever the mldonkey folder is...IE /share/mldonky  then add /mlnet  so you would have /share/mldonkey/mlnet and hit enter. MLDonkey is now running.

 Step 5. You have many options here. I'll give two easy ones.
   5a. Open a web browser and type in 127.0.0.1:4080 as the address. It will be obviouss from there. [assuming 4080 is still the web interface default]
   5b. Run KMLdonkey {or install and run}. If it is the first time you should be in the wizard, if you have run it before you will find the wizard under settings 'KMLDonkey setup wizard' or with focus on KMLDonkey hold shift and hit K. Follow the wizard and enter /share/mldonkey as your working directory, and /share/mldonkey/mlnet as your core. You should be all set. [ most often when running KMLDonkey under Gnome it will not automatically start the core. But no worries just start it from the command line/run/or create launcher]
  5c. run or install any number of other GUIs for MLDonkey.

 REPLACE ALL DIRECTORIES WITH THE ONES YOU USE

 This should work for most people. I have not yet done this in ubuntu but I have done it this way under SUSE, Mandriva, Debian, Yoper, Mepis, and others. I think I remeber it working everytime.


thanks for the website info... did not know how to start the app... did not know that there is no default gui when you install mldonkey-server

---

### Post by buildid on 2006-02-13
[URL="http://mldonkey.sourceforge.net/CompilationProblems#configure_op
tions"]configure_options[/URL] install mldonkey Howto for ubuntu ......

for any gui/skin : have a look [here]("http://mldonkey.sourceforge.net/DownloadLinks#Third_party_cores.2C_GUIs.2C_Distributions")

just switch after 3 months from amule to mldonkey , but i always switch between : edonkey2000/amule/mldonkey .....

newest version from cvs works great Bittorrent plugin do what it have to do ...iam satisfied..

---

### Post by Harry_Sack on 2006-02-24
thanks will try this

---

