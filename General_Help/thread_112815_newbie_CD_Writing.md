---
title: "newbie: CD Writing ?"
date: 2006-01-05
forum: General Help
---

### Post by petef on 2006-01-05
Hiya,

Im new to Linux\Ubuntu and have had it installed on a machine at work and one at home for a couple of weeks. The machine I have at home has just the basic installation as I don't currently have internet access but I do have a CD writer and CD drive. I tried last night to copy an audio CD (one which I own the copy was just a test) but found that when the CD is inserted it opens Sound juicer and I have to extract the data as an ogg file and then write this to the CD ? How do I just make an exact copy of a CD to play in other standard players ? 

Would I be better using Gnomebaker ?

Thanks

Pete

---

### Post by cvcaelen on 2006-01-05
Hi, 

The answer is right here:

[http://easylinux.info/wiki/Ubuntu#How_to_install_CD.2FDVD_Burning_Application_.28GnomeBaker.29](http://easylinux.info/wiki/Ubuntu#How_to_install_CD.2FDVD_Burning_Application_.28GnomeBaker.29)

Have fun

Christiaan

---

### Post by petef on 2006-01-05
Thanks for the reply Christiaan :D 

Is their a way I can just download the complete version of Gnomebaker and install it at home as I currently don't have an internet connection to us apt-get\synaptic etc

Cheers

Pete

---

### Post by StefanoCole on 2006-01-05
Well I did in this way: I downloaded from a Windows box connected to internet the following packages:
cdda2wav, gnomebaker, mpg321, sox, vorbis-tools. Then, I have created a local repository on my Ubuntu box at home with the above packages (there should be a Wiki or Howto on how to create a local repo). And then I installed gnomebaker from the local repo using synaptic. Note: I downloaded gnomebaker from Dapper Drake archives (gnomebaker_0.5.0-3_i386.deb)because the version in Breezy had a bug and it didn't work for me.
But, if you simply want to record an audio CD you could try to use the application already available in Breezy (Serpentine). Unfortunately for me I was not succesful in recording with Serpentine, but it could work in your case.

Bye, Stefano

---

### Post by petef on 2006-01-05
I have tried Serpentine but found I couldn't get it to see the audio CD ?

I will try your other suggestion of creating a local repo

Cheers

Pete:)

---

### Post by pappo on 2006-01-05
You can also use the command line method.

1.  Get each package ( .deb) files from the internet and copy them to any directory on your ubuntu machine.

2.  cd to that "any directory".

3.  use "sudo dpkg -i gnomebaker.deb" (or whatever the package name is)
    that will install each package.

good luck

---

### Post by StefanoCole on 2006-01-05
Pete, before running Serpentine do the following:
- extract to hard disc the audio tracks as wav files (if you cannot do this using Soundjuicer you can try with "cdparanoia -B && eject" from a terminal: it will rip the current CD in the drive to the current directory, in separate WAV files)
Then you can run Serpentine to create an audio CD from the wav files.
Or, if Serpentine doesn't work, to burn the CD just type (from terminal):
cdrecord dev=device-name *.wav
Replace device-name with the device name for your cd burner [/dev/hdc on my machine].

Stefano

---

### Post by petef on 2006-01-05
That's what I love about Ubuntu Linux so far any question I have is answered comprehensively in seconds :) Thanks guys

I will give the above options a try, I want to learn more things in the Terminal so will check that out first. 

:D 

Pete

---

