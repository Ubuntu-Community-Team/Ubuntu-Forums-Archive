---
title: "HOWTO: Steem (St emulator) + Sound"
date: 2007-09-21
forum: Gaming &amp; Leisure
---

### Post by mikeym on 2007-09-21
Hi All,

I was a big fan of Steem for Windows so I was excited when I discovered there was a Linux version out XSteem, but I found out that most people had been having problems getting it working with sound. 

So here's my guide on setting it up:

GO to the[ Steem website downloads page]("http://steem.atari.st/download.htm") and download what it recommends and save xsteem. Extract the contents of the xsteem archive where you want steem to be.

You can use the commands from the terminal: 

```

mkdir steem
cp xsteem*.tar.gz steem
cd steem
tar -zxvf xsteem*.tar.gz

```


When you first run steem it gives you a list of things to choose and directories to select to set up steem. it doesn't give you the option of creating new directories so your best to do so before hand.

Create in the steem directory 'disks' and 'hd1', from the terminal:

```

mkdir disks
mkdir hd1

```


Start steem by running the 'steem' executable. From the command line:

```

./steem

```

Select the directories you have made and select your TOS (the BIOS of ST's).

To get sound working install [PortAudio]("http://www.portaudio.com/download.html"). I have tried to make debs for you -

I'm not good at this and I have only used 'checkinstall' to make these packages so they may not work very well, but portaudio is not used by the ubuntu packages and shouldn't mess up anything (you can always remove it later from synaptec).

Download the version for your system 
(32bit) [portaudio_19_061121-1_i386.deb]("http://ubuntuforums.org/attachment.php?attachmentid=43997&stc=1&d=1190371506") 
(AMD 64 bit) [portaudio_19_061121-1_amd64.deb]("http://ubuntuforums.org/attachment.php?attachmentid=43996&stc=1&d=1190371506")

Then install it, from the terminal (find where you download it first):

```

dpkg -i portaudio_19_061121-1*.deb

```

You may need to restart X or reboot for the changes to the audio packages to work. 

Read the [Beginners guide at steem]("http://steem.atari.st/beginners.htm") to find out how to set up steem to run your games.

Enjoy

---

