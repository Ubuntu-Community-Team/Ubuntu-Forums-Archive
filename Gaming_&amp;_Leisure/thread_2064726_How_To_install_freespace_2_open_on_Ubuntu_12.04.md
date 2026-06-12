---
title: "How To install freespace 2 open on Ubuntu 12.04"
date: 2012-09-30
forum: Gaming &amp; Leisure
---

### Post by abid_naqvi83 on 2012-09-30
FSO (Freespace 2 Open, aka Freespace SCP) is an awesome project. Its awesomeness however fails to extend to its installation process. After considerable trials and tribulations I finally managed to install FSO and the freespace 1 port (Descent: The Great War) on Ubuntu 12.04 (running on an ancient Dell laptop with an intel 945GM integrated graphics card).

Here are the steps I took. Be warned that there were many dead-ends and U-turns so this procedure is not guaranteed. Feel free to post questions and suggestions if the procedure fails.

**Objective**: Install the FSO engine and use it to run the Freespace 2 (Retail) game and fsport (freespace open port which ports the retail Freespace 1 game to the opensource engine).

**Resources**: Running the FSO engine requires game-files from the retail Freespace 2 installation which can be acquired from either old copies of the Freespace 2 (Retail) CD, a Windows installation of the game you have access to or by buying a copy from [www.gog.com](www.gog.com) (Good Old Games) for just $5.99.

**Procedure**:

**1.** Create the folder that will contain the freespace 2 engine and various games files. I chose $HOME/Games/freespace2

```
mkdir $HOME/Games/freespace2

export FS2="$HOME"/Games/freespace2
```

$FS2 should now refer to the folder you chose to install the engine and files in.

Now we need to move the game files from the Freespace 2 Retail installation. I will only outline the [www.gog.com](www.gog.com) and wine procedure for acquiring game files since that is the only one I am familiar one. The technique for getting game files from a Windows installation should be pretty similar. The internet contains information on extracting game files directly from a CD (for example [http://hyperlogos.org/page/Freespace-2-Open-Ubuntu-Feisty]("http://hyperlogos.org/page/Freespace-2-Open-Ubuntu-Feisty")).

**2.** For the wine procedure navigate to [http://www.gog.com/en/gamecard/freespace_2]("http://www.gog.com/en/gamecard/freespace_2"), buy and download the windows installer (.exe file).

**3.** Now execute the setup file using wine by navigating to the folder containing the setup exe file and running the following in the terminal:

```
wine ./setup_freespace_2.exe
```

This will run the installer under wine. Complete the installation and locate the folder containing the game files. On my computer it was located at:

```
export $WINE_FS2="$HOME"/.wine/drive_c/Program\ Files/GOG.com/Freespace\ 2
```

$WINE_FS2 should contain the absolute path to the wine folder containing the Freespace 2 (Retail) game files (i.e. the one containing the game launcher exe file). It isn't necessary that the game run under wine (it didn't for me).

**4.** We now create the requisite directory structure in the freespace2 game folder and copy the required game files from the wine installation as follows:

```
mkdir -p $FS2/data/players

cd $WINE_FS2

cp Root_fs2.vp $FS2/data/root_fs2.vp

cp smarty_fs2.vp sparky_fs2.vp sparky_hi_fs2.vp stu_fs2.vp tango1_fs2.vp tango2_fs2.vp tango3_fs2.vp warble_fs2.vp $FS2/data/

cp data2/tangoA_fs2.vp $FS2/data/tangoa_fs2.vp

cp data3/tangoB_fs2.vp $FS2/data/tangob_fs2.vp

cp data/players/*.hcf $FS2/data/players/

```

(Note: All the files in to $FS2/data must have filenames that are entirely in small-case)

**5.** We create and populate the configuration file for the Freespace 2 Open Engine:

```
mkdir $HOME/.fs2_open

cat > $HOME/.fs2_open/fs2_open.ini << "EOF"
[Default]
VideocardFs2open=OGL -(1680x1050)x32 bit
EOF
```

Replace the screen resolution (1680x1050) with your computer's.

**6.** Download the freespace 2 open Linux binary from [fs2_open_3_6_12]("http://swc.fs2downloads.com/builds/LINUX/fs2_open_3_6_12_INF.tar.bz2"). Extract the archive in $FS2.

Simply, copy the downloaded *fs2_open_3_6_12_INF.tar.bz2* file to the $FS2 folder and extract the files using:

```
cd $FS2

tar -jxf fs2_open_3_6_12_INF.tar.bz2
```

The archive contains two launchers (binaries that launch the freespace 2 open engine and uses it to run the Freespace 2 (Retail) game natively on Linux). The '_r' version is the one to use, the '_d' version is the debug version which creates an fs2_open.log file to help in debugging.

**7.** Test the launcher by executing the binary:

```
./fs2_open_3_6_12_INF_r
```

This should launch Freespace 2 (Retail) using the FSO engine. Enjoy the game.

**References**: 

[http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux/Quickstart]("http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux/Quickstart")
[http://hyperlogos.org/page/Freespace-2-Open-Ubuntu-Feisty]("http://hyperlogos.org/page/Freespace-2-Open-Ubuntu-Feisty")
[http://fsport.hard-light.net/website/downloads.html]("http://fsport.hard-light.net/website/downloads.html")

---

### Post by abid_naqvi83 on 2012-09-30
The next step is to configure FSO to play fsport (the Freespace port of the retail 1st version of the game subtitled: "Descent: The Great War").

Before we begin a couple of things to note. It is advised that one create separate pilots (characters) to play Freespace 2 (Retail) and fsport on the FSO engine. Additionally playing one game can mess up the settings for the other. If this happens the easiest solution is to navigate to *$HOME/.fs2_open* and delete everything but the .ini files in the main folder.

**1.** There are issues with FSO binaries and supporting various mods. The binary we installed to play Freespace 2 (Retail) won't work with mods, so we begin by downloading a binary that will work: [fso_5395.zip]("http://www.joskus.jossain.com/fso_5395.zip")

Copy the zipped archive to $FS2 and unzip it.

```
unzip fso_5395.zip
```

This will extract the *fs2_open_5395_r* binary. This is the binary to use when playing mods.

**2.** Launching FSO to play a mod is a slightly complicated process which includes specifying the mod and the various options to enable. The developers have created a GUI Launcher that allows one to choose the binary, the mod and the options with ease. The next step is to install this GUI Launcher. Unfortunately this will involve compiling YAL from source checked out using svn (which in turn requires dependencies to be fulfilled), which one does as follows:

```
mkdir $HOME/tmp_yal

cd $HOME/tmp_yal

sudo apt-get install build-essential automake1.9 autoconf libreadline6-dev subversion

svn checkout svn://vega.livecd.pl/yal/trunk     # Downloading yal source material

cd trunk

./autogen.sh      # Compiling the source to create fs2 launcher

cp bin/fs2_launcher $FS2      # Copy fs2 launcher to game folder

cd $FS2

rm -r $HOME/tmp_yal       # Optional: Delete source and compilation
```

**3.** Now we download the game files for the fsport. First create the directory that will contain the files.

```
mkdir $FS2/fsport3_3

export $FSport="$FS2/fsport3_3
```

Now navigate to [http://fsport.hard-light.net/website/downloads.html]("http://fsport.hard-light.net/website/downloads.html") and download the following files:

[INDENT][I]fsports3_3.zip
fsport-missions.zip
sparky_hi_fs1.zip
warble_fs1.zip
tango_fs1.zip
stu_fs1.zip
odeon_fs1.zip[/I][/INDENT]

Move all these zip files to $FSport and unzip them:

```
cd $FSport

for file in *.zip
do
unzip $file
done

rm *.zip    # Optional: Delete zip files.
```

**4.** Finally we test the installation by running

```
./fs2_launcher
```

This will open up the GUI which takes about half a minute to launch on my relatively ancient laptop. To run fsport click on 'Browse' and navigate to $FS2. Choose *fs2_open_5395_r*.

Click on the *MOD* radio button followed by the *Select MOD* button. Choose *fsport3_3* from the list.

Click *Run* at the bottom to launch the game. You should be playing fsport. Enjoy.

---

### Post by em3raldxiii on 2012-11-20
Dude, this is an awesome tutorial.  You should be commended for your efforts, and for such a thorough write-up.  I am going to follow your tutorial to the letter (obviously changing the things that are system-specific for me) and I will post here how it goes.  This will take place sometime soon, perhaps tomorrow since it's 2am.

But anyway, I just wanted you to know that your efforts have not gone unnoticed :D

-Mike

---

### Post by Rushlight on 2013-04-12
I converted my whole Computer to Ubuntu, and ive been trying to Get FS to work. i had FSOpen on my pc, and the original windows partition of my HD is still intact(although windows isnt, i cant fix it, long story) , so i have all the files, the open, AND the original discs. i tired the first downlowad sugested for FS2 here and put the files in the directory, but Ubuntu wont let me run them as executables, or at all. My cpu isnt powerful enough to emulate it with wine.

Can someone walk me step by step on how to get FS2 open to run if you have all the original files already installed?

---

### Post by ajbader on 2013-04-20
No one needs to walk you through it. I just got mine to work (just Freespace 2). You probably just forgot to make your files excutable. You can open them in the file manager > permissions and check mark the the excutable box. It should work after that.  If something doesn't work, a good idea would be to run it in the terminal. Things like this would become blatantly obvious that way.  Also great job on the tutorial. Too bad in only a few short months, major changes have impacted QT and qtmake doesn't function the same way when you wrote this tutorial.

---

