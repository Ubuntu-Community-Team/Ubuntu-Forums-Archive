---
title: "Ubuntu with minimal to run VirtualBox"
date: 2010-02-18
forum: Desktop Environments
---

### Post by Data-Base on 2010-02-18
Hello,

I are thinking to setup some PCs for testing stuff in Virtualbox

what I need is Ubuntu with minimal setup just to run VirtualBox in GUI mod no need for any Office or apps or pretty stuff

I like to just start the machine and it will ask for log-in info then starts the virtual box so I can chose to install/start/edit VMs the way I like

I'm going to start working on it, I just need a good advice about the best approach :-)

1- Ubuntu Server with minimal install (any other minimal)?
2- Windows Manager (no need for Openbox or any other light DE)?
3- VirtualBox
4- script to start VirtualBox after log-in

is there any thing else I have to think about?

---

### Post by Hero of Time on 2010-02-18
I found that even with the 'minimal' installation switch, it still installs more things than you would actually need. You can pick any installer you want, personally, I would go with a desktop install disc, the alternative one. Using F6, you can select expert mode which lets you go through the installation one step at a time, asking to confirm the next step and allows you to skip one or two too.

I follow the install one step at a time until it comes to installing the base system. The first installation part is needed, else you won't have anything to work with. After that, it will point you to installing additional software and packages (without selecting minimal or command line at the beginning with F4, it will install the entire desktop environment). Skip this one. Configure apt as you would normally, I answer 'yes' to all questions so I have the most software available, but that's up to you. Install the bootloader of your choice and finish the installation.

Now that you're done, you have two things left to do: copy or move sources.list.apt-setup to sources.list, disable the CD-rom lookup (in case you have internet, no need to install older versions from the CD) and after that install the software you need. I use aptitude, because it lets you select packages to install the same way Synaptic does. Because of that, you can install xorg without all the input and video drivers that you don't need. Mark it for install and scroll down to unmark the drivers that you don't need.

You can go for a desktop manager by selecting only the needed packages. For example, go for Xfce4 and install xfce4-session (so you can auto-start VB) and xfwm4 (so you can move windows around and change it's size). Xterm should be installed too, or any other terminal emulator.

Now you're ready to add the VB repository if you want to use the PUEL version so you have USB support, or simply install the OSE from the Ubuntu repo (I suggest you use the VB repo, always up2date with that one). Any missing dependencies like Qt will be installed automatically.

Partitioning and configuration for network and all is all up to you. You can pick any desktop/window manager you want. Other lightweight alternatives are LXDE, OpenBox, FluxBox, IceWM, WindowMaker and the likes.

---

### Post by Data-Base on 2010-02-18
Hello!

thank you **Hero of Time**,

here what I did so far

I installed Ubuntu 8.04 LTS Server (hardy) and chosen not to install anything other than OpenSSH

then I did the following

```
sudo apt-get update
sudo apt-get upgrade
```
to update the system



```
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install make gcc
```
install the headers
install make and gcc to compile any kernel extension virtulabox may need

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```
backup the apt source file just in-case ;-)

```
sudo echo "" >> /etc/apt/sources.list
sudo echo "" >> /etc/apt/sources.list
sudo echo "# VirtualBox" >> /etc/apt/sources.list
sudo echo "deb http://download.virtualbox.org/virtualbox/debian hardy non-free" >> /etc/apt/sources.list
```
adding the VirtualBox reps.
note: make sure you chose the right rep. (hardy in my case)

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```
get the Sun key


```
apt-get install xorg virtualbox-3.1
```
the final step to install Xorg and VirtualBox

_IF_ you get error
you may need to run the command below to recompile the kernel extensions
```
sudo /etc/init.d/vboxdrv setup
```

a rebot will not hurt ;-)

to use VirtualBox
I used
> startx
then
```
VirtualBox
```

looks ugly, but I will see what I can do :-)

please feel free to correct me and help me to make it better :-)



cheers

---

### Post by Hero of Time on 2010-02-18
Whatever works for you. But I personally add 3rd party repos to /etc/apt/sources.list.d/<name>.list. VB would be /etc/apt/sources.list.d/virtualbox.list. That way, you can spot the different repos a lot easier in case you need to remove one or make a change.

---

### Post by Data-Base on 2010-02-21
> **Hero of Time said:**
> Whatever works for you. But I personally add 3rd party repos to /etc/apt/sources.list.d/<name>.list. VB would be /etc/apt/sources.list.d/virtualbox.list. That way, you can spot the different repos a lot easier in case you need to remove one or make a change.

That is cool, I did not know about this trick
Thanks allot :-)

---

### Post by RedSquirrel on 2010-02-21
> **Data-Base said:**
> 

```
sudo echo "" >> /etc/apt/sources.list
sudo echo "" >> /etc/apt/sources.list
sudo echo "# VirtualBox" >> /etc/apt/sources.list
sudo echo "deb http://download.virtualbox.org/virtualbox/debian hardy non-free" >> /etc/apt/sources.list
```adding the VirtualBox reps.
note: make sure you chose the right rep. (hardy in my case)

You can't use redirection in this manner. The sudo applies to the echo, but not to the redirection.

However, you can use 'tee', like this:

```
echo "# VirtualBox" | sudo tee -a /etc/apt/sources.list
```

---

### Post by Data-Base on 2010-02-24
> **RedSquirrel said:**
> You can't use redirection in this manner. The sudo applies to the echo, but not to the redirection.

However, you can use 'tee', like this:

```
echo "# VirtualBox" | sudo tee -a /etc/apt/sources.list
```

thanks again guys it is really nice that you are helping people to learn more :-)

---

### Post by Advice Pro on 2012-08-07
> **Hero of Time said:**
> I personally add 3rd party repos to /etc/apt/sources.list.d/<name>.list.

How did you do this?

---

### Post by wildmanne39 on 2012-08-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

