---
title: "How I installed Mathematica 8 in Linux (Ubuntu 10.10)"
date: 2010-12-02
forum: Education &amp; Science
---

### Post by rewyllys on 2010-12-02
Having purchased Mathematica 8 for Linux from Wolfram Research, Inc. ([www.wolfram.com]("http://www.wolfram.com")), I downloaded the following file:
 

 Mathematica_8.0.0_LINUX_MachineSpecific.sh
 

 Next, to help guard against file loss, I copied this file to a DVD-R disk, which I named
 

 Mathematica_8_Linux
 

 With this DVD in my disk drive, "/media", and following instructions available on the Wolfram Website, I used "sudo gnome-terminal" in a Terminal session to open a second session as root.   As root, I used  
 

 chmod +x Mathematica_8.0.0_LINUX_MachineSpecific.sh  
 

 to make this file executable (this is an important step).
 

 Next, as root I moved to directory "/usr/local" and issued the command
 

 sh /media/Mathematica_8_Linux/Mathematica_8.0.0_LINUX_MachineSpecific.sh 
 

 in order to execute the installation script.  Thereafter, I responded to the prompts from the installation script, accepting the default options offered by the script, since they suited my situation.

---

### Post by nitrogensixteen on 2011-01-30
If the installer will not allow you to register following Activation,
```
sudo rm -r /usr/local/Wolfram/Mathematica
sudo rm -r $HOME/.Mathematica
cd /usr/local
sudo sh $PATH_TO_INSTALLER
```
choose install directories
while activating, either
1)
 ```
sudo nano /usr/local/Wolfram/Mathematica/Licensing/mathpass
```
2)
 ```
nano $HOME/Mathematica/Licensing/mathpass
```
file format is:
hostname    MATHID    LICENSE_NUMBER    PASSWORD
then complete activation and registration

no idea why this problem occurred but this will allow it to load.

---

### Post by nitrogensixteen on 2011-01-30
Additionally, in the event that CUDALink will not work:
Follow the instructions in this forum for manual installation of nvidia devdriver's vice the ubuntu supplied package, ubuntu package puts libraries in non-standard locations.

Install the cuda sdk and then make the gpucomputing examples to verify cuda is available and nvcc is configured, executing more resource hungry applications will require adding "vmalloc=256mb" or some larger allocation in your linux grub commandline.

Open a new notebook in Mathematica and execute:
```
Needs["CUDALink`"]
CUDAQ[]
```
This may return false.

If the stderr in the terminal you ran mathematica from spits out garbage about cuInit being undefined symbol from the mathematica cudalink_single/double library, then libcudart is not loaded and exporting the cuInit routine which initializes cuda. add the following to your .bashrc
```
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib
LD_PRELOAD=$LD_PRELOAD:/usr/local/cuda/lib/libcudart.so
```

after that run a new terminal or reload the environment and run Mathematica again, execute the same commands and it should return true.
```
SystemInformation[]
```
Will bring up info about your cuda machines under links->cuda.

---

### Post by jbbishop2 on 2011-02-19
Hello, and thank you for posting your installation method. 

I'm having problems trying to install Mathematica 8.0 on Ubuntu 10.04.  I downloaded a copy of Mathematica_8.0.0_Student_LINUX.sh from the Wolfram site to the desktop.  Double-clicking on the icon opened a dialog box offering to run in a terminal window, or just Run, cancel, etc.  I've tried selecting both Run and Run in a terminal window, either will start the installer.  It verifies archive integrity for a while, then starts installing.  When it gets to the first question about where to install the files, I try Enter to select the default. It comes back saying it cannot create the directory, suggests I need to be logged in as root, and asks again.  Hitting Enter each time just repeats the question, trying anything else (including sudo -s, trying to get to the root) brings "Create directory (y/n)?" Answering y allows it to continue.  Same sort of questions and responses for the script directory, and then it says it's done installing.  After which I can't find anything that looks like it installed anywhere.

So, the installer appears to run, I just can't get it to create the directories.  It must be something simple and I'm sorry to be so thick, but where am I going wrong?

Thanks,
John

---

### Post by jbuceta on 2011-02-24
Hi there,

*I have installed Mathematica 8 in Ubuntu 10.10
*I have also installed CUDA sdk, driver...and the test are working fine
*My GPU is fully supported my Mathematica (TESLA C1060)
*I have also checked that the environment variables are well defined
* Now the problem is:

Mathematica says that cuda library is loaded but can not be initialized, any clue?

Cheers,

J

---

### Post by rewyllys on 2011-02-26
> **jbbishop2 said:**
> Hello, and thank you for posting your installation method . . . . When it gets to the first question about where to install the files, I try Enter to select the default. It comes back saying it cannot create the directory, suggests I need to be logged in as root, and asks again. . . .

I'd suggest that you try starting the whole installation by using "sudo gnome-terminal", so that you're doing the installation as root.

---

### Post by Boulemans on 2011-03-19
> **nitrogensixteen said:**
> 
while activating, either
1)
 ```
sudo nano /usr/local/Wolfram/Mathematica/Licensing/mathpass
```
2)
 ```
nano $HOME/Mathematica/Licensing/mathpass
```
file format is:
hostname    MATHID    LICENSE_NUMBER    PASSWORD
then complete activation and registration

What do you mean with this line? I've installed Mathematica 8 with a .sh file, then I've created the /usr/local/Wolfram/Mathematica/Licensing/ directory, touched the mathpassfile. Then I've run mathematica, filled in the fields in the GUI and in the mathpass text file I've typed:

"hostname \tab \mathid \tab \license_number \tab \pw", where I've used the logical numbers for mathid, license_number and pw.

But this doesn't work for me. I am still stuck with the "Get access to your benefits. Register Mathematica now!" page.

---

### Post by justanotherhandle on 2011-04-01
I know that this is an old(er) thread, but I just wanted to thank rewyllys and nitrogensixteen for posting. With the information provided I was able to successfully install Mathematica 8.

Much appreciated!

---

### Post by rewyllys on 2011-04-02
You're most welcome!

---

### Post by nishthedevil on 2011-04-15
Hi, there,

Well mathematica 8 has a new field called activation key as opposed to license number and am having problem getting it activated, 
can anyone help me on this please

---

### Post by rewyllys on 2011-04-18
> **nishthedevil said:**
> Hi, there,

Well mathematica 8 has a new field called activation key as opposed to license number and am having problem getting it activated, 
can anyone help me on this please
I suggest that you contact Wolfram, Inc., directly to ascertain your activation key.

---

### Post by LowDepth on 2011-04-26
For me the only way to get beyond the registration screen was to install Mathematica 7, do the registration in the textbased v7 installer and than just install V8. 
After I installed V7 Mathematica 8 just used the data entered for v7. I don´t know, if this works for V7 trial versions as well, but you should try it. I´m lucky enough to own both, 7 and 8.

---

### Post by AndroidOcean on 2011-05-11
Hello, I think I have a fix for the problem of not having the root account.

So I am new to Ubuntu, so dont mind my work if it seems sloppy.

Here is the breakdown:

First, I had the files on an Iso, so I mounted them.

Next, I attempted to open the files from the GIO, but no avail, so i opened terminal and run into the problem everyone else did.. I searched for some commands, and here is what I got in order to install Wolfram Mathematica.

I changed directory to where my file was, I just did cd .. until I was back to /, then I changed directory until I got to the Install folder, with the cd command, finally, I used this code to install

```

sudo ./MathInstaller

```

---

### Post by Fixman on 2011-05-16
I am trying to install Mathematica 8, but I have a different problem. I can activate the program both as root and as a normal user, but in both cases it keeps stuck in the "Product Registration" page. I have three buttons (Don't ask me again, register later, register now), but none of them does anything.

Can anyone help me here?

---

### Post by sedo_5 on 2011-05-23
Hi everyone :)
Has anyone solved the problem of how to skip the registration window, after licensing?
It's a problem related to some libs, i suppose, or to java maybe...
For those who don't know about this problem:
after licensing, you get a window where you can choose to register the product now or later, but clicking on any of the buttons on the screen leads to no action!
Has anyone got some clue?
Would be really interesting knowing why of this behaviour...

Thanks :)
Renzo

---

### Post by am_i_registered on 2011-05-24
hi, i you re stuck at the registration screen... try sudo mathematica in the terminal.

---

### Post by tiagogds on 2011-07-06
> **Boulemans said:**
> 

But this doesn't work for me. I am still stuck with the "Get access to your benefits. Register Mathematica now!" page.

I had the same problem on my debian sqeeze. The way I solve this is the folowing:

Remove the openjdk-6-jre package

Install (or reinstall) sun-java6-jre

Run the mathematica again.

---

### Post by BeRoot ReBoot on 2011-08-08
> **tiagogds said:**
> I had the same problem on my debian sqeeze. The way I solve this is the folowing:

Remove the openjdk-6-jre package

Install (or reinstall) sun-java6-jre

Run the mathematica again.


This didn't work for me. Neither did running it with sudo, or the OP's solution. Still stuck at the Register Now screen.

Any other ideas?

---

### Post by nitrogensixteen on 2011-08-11
Try installing with a different window manager(or compositor) and jre, like the sun jdk. I had this problem long ago and can't remember how i fixed it. Had to reinstall.

---

### Post by wendy.willow on 2011-08-12
I have the same problem and none of these suggestion worked. I am still stuck on the Wolfram Product Registration dialog.

Anyone? I'm beginning to be extremely frustrated.

---

### Post by dyoxin on 2011-08-13
I'm also stuck on the &quot;Product Registration&quot;. (I'm using Gentoo, so it isn't an Ubuntu-specific issue)

---

### Post by BeRoot ReBoot on 2011-08-21
bump, anyone have the slightest idea what's wrong here?

As a side note, I've been using wxMaxima (it's in the repos) for my Mathematics and Physics needs since Mathematica has failed me. It's an OK replacement for my needs and I will be using it in my classes instead of relying on uni-provided Mathematica licences to teach this semester (I'm an instructor for Linear Algebra 101 & 102 and Modern Physics). Seeing as how Maxima is Free, open source software, I'd encourage all current Mathematica users on Linux to evaluate whether their needs are better served by a Free product.

By the way, can the OP unmark this thread [SOLVED]?

---

### Post by evanigma on 2011-09-14
Following the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=11025001&postcount=2") helped me to get past the registration screen.

---

### Post by rewyllys on 2011-11-02
Users of Mathematica 8.0.0 may be interested in knowing that a free update to v. 8.0.4 is available *during* November 2011.  For information, check
[http://user.wolfram.com/portal/upgrade.html](http://user.wolfram.com/portal/upgrade.html)

---

### Post by dboonz on 2012-01-25
Hi,

I've installed mathematica as root, and it works fine, only the manipulate command does not work: I can't change the sliders. Has anyone else had this problem too? Any solutions?

regards,

Dirk

---

### Post by rewyllys on 2012-01-25
> **dboonz said:**
> Hi,

I've installed mathematica as root, and it works fine, only the manipulate command does not work: I can't change the sliders. Has anyone else had this problem too? Any solutions?

regards,

Dirk
Have you downloaded and installed the Wolfram *CDF Player*?  Its URL is:
 
[http://demonstrations.wolfram.com/download-cdf-player.html](http://demonstrations.wolfram.com/download-cdf-player.html)

Adding this player should do the trick.

---

### Post by asadig on 2012-03-08
After removing openjdk-6-jre and installing sun-java6-jre
I am still stuck with the "Get access to your benefits" page

---

