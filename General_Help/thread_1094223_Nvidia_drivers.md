---
title: "Nvidia drivers"
date: 2009-03-12
forum: General Help
---

### Post by lozzy on 2009-03-12
PLEASE HELP ME I AM SO LOST.......

I am still not getting the correct screen resolution using ubuntu... my monitor goes up to 1028x1024 but ubuntu preferences only go as far as 960x600.

I dont really understand ubuntu way of working as have used xp for so long....

I have downloaded nvidia driver as was told this may solve the issue..... But i have NO clue how to actualluy install it.......??? PLEASE can someone guide me thru it with simple non technical instructions???? 

Its the same for other things that i have downloaded... i dont have a clue what to do .......

thanks :(

---

### Post by Neo_The_User on 2009-03-12
The nVIDIA drivers are terrible, hard to use, and make your computer boot up in low graphics mode every reboot 3 out of 5 times. If that's your only card and your only option, use the open source nVIDIA drivers. If you really need the nvidia drivers, install the nVIDIA drivers from the website. Here is how. write all this down on paper before proceeding.

Terminal:

```

sudo /etc/init.d/gdm stop

```

Now you should be in command line.

```

links http://www.nvidia.com/Download/index.aspx?lang=en-us

```

Select your driver and follow the instructions in the driver page after choosing what graphics card you have.

You will need these tools to install the nvidia drivers:

```

sudo apt-get install build-essential dh-make debconf debhelper xorg-dev

```

I hope this guide is simple enough. If you need further help or an easier guide that explains everything much better, let me know.

---

### Post by Vadi on 2009-03-12
Here is a simpler solution.

Go to System &#9656; Administration &#9656; Hardware Drivers, and press the 'Activate' button for an nVidia driver.

---

### Post by Neo_The_User on 2009-03-12
> **Vadi said:**
> Here is a simpler solution.

Go to System &#9656; Administration &#9656; Hardware Drivers, and press the 'Activate' button for an nVidia driver.

Those drivers are old. I hate the drivers no matter what they are from the repos.

---

### Post by Vadi on 2009-03-12
> **Neo_The_User said:**
> Those drivers are old. I hate the drivers no matter what they are from the repos.

The are 180 drivers if needed. That said, it's a) not good to recommend beta drivers to new users and b) using a text-only browser to computer-inept people, casually mentioning "I hope this guide is simple enough.", because it is not to someone who's not an ace, and c) personal opinion has no place in assisting help.

---

### Post by lozzy on 2009-03-12
> **Vadi said:**
> The are 180 drivers if needed. That said, it's a) not good to recommend beta drivers to new users and b) using a text-only browser to computer-inept people, casually mentioning "I hope this guide is simple enough.", because it is not to someone who's not an ace, and c) personal opinion has no place in assisting help.

im so confused .... so what do i need to do??? 

there are no proprietary drivers on the pc ??

---

### Post by Neo_The_User on 2009-03-12
> **lozzy said:**
> im so confused .... so what do i need to do??? 

there are no proprietary drivers on the pc ??

Exactly why am I right in this situation. Ubuntu isn't smart enough to match your PC with a driver so follow my guide and do it that way. What GPU do you have btw? nVIDIA 8800 Ultra? 5900 XT? etc. there are like 50. And Vadi, its not my personal opinion. Those drivers are old. And I said in that post right after I said "I hope its simple enough" that I would explain it more and dumb it down.

---

### Post by lozzy on 2009-03-12
> **Neo_The_User said:**
> Exactly why am I right in this situation. Ubuntu isn't smart enough to match your PC with a driver so follow my guide and do it that way. What GPU do you have btw? nVIDIA 8800 Ultra? 5900 XT? etc. there are like 50. And Vadi, its not my personal opinion. Those drivers are old.

i dont know what u mean ??

---

### Post by Neo_The_User on 2009-03-12
> **lozzy said:**
> i dont know what u mean ??

What model is your graphics card by nVIDIA? It should be the big green case looking device inside your computer that says nVIDIA on it with an attractive computer drawn girl on it.

---

### Post by Vadi on 2009-03-12
[Click here to install hardinfo]("apt:hardinfo")

Then, go to System &#9656; preferences &#9656; system profiler and benchmark (or applications &#9656; tools &#9656; hardinfo), and click on 'Generate report'. Make sure that Computer and Devices are selected, but *not* benchmarks.

It'll then made a hardinfo_report.html file where you ask it to - attach this file to the post here.

@Neo_The_User: Expecting someone to be able to navigate with links when they can't tell what their card is? Heh. Old drivers? They aren't even a year old.

---

### Post by Neo_The_User on 2009-03-12
> **Vadi said:**
> [Click here to install hardinfo]("apt:hardinfo")

Then, go to System &#9656; preferences &#9656; system profiler and benchmark (or applications &#9656; tools &#9656; hardinfo), and click on 'Generate report'. Make sure that Computer and Devices are selected, but *not* benchmarks.

It'll then made a hardinfo_report.html file where you ask it to - attach this file to the post here.

@Neo_The_User: Expecting someone to be able to navigate with links when they can't tell what their card is? Heh. Old drivers? They aren't even a year old.

I said I would explain if he needed help FOR THE LAST TIME. Now you, I wouldnt expalin to, Vadi. I wouldn't write you a simple guide because you'd just give me hard time like you are doing now. Lozzy, I'm sorry for this little argument me and Vadi are having as if we were two little school girls yelling at each other out front on the sidewalk.

---

### Post by lozzy on 2009-03-12
> **Neo_The_User said:**
> I said I would explain if he needed help FOR THE LAST TIME. Now you, I wouldnt expalin to, Vadi. I wouldn't write you a simple guide because you'd just give me hard time like you are doing now. Lozzy, I'm sorry for this little argument me and Vadi are having as if we were two little school girls yelling at each other out front on the sidewalk.

ummm?? ok.. im stil no further on...just baffled by all this techo stuff.. i just want to get the rite screen res#-o

---

### Post by Neo_The_User on 2009-03-12
OK Go to Applications > Accessories > Terminal and type in this:

```

sudo /etc/init.d/gdm stop

```

Now this will make your screen all black with white text which is called "command line" also referred to as cli.

Now type this in when you get into command line.
```

links http://www.nvidia.com/Download/index.aspx?lang=en-us

```

Another way you could download the drivers is to download the drivers graphically using a program called firefox. This will make things easier. After you downloaded the drivers, save the drivers to your hard drive. Your hard drive consists of blocks of memory of which data is stored to. Save the drivers to your home folder. It should be in /home/lozzy or something like that.

Select your driver and follow the instructions in the driver page after choosing what graphics card you have. Check inside your computer to find out or run lspci from command line.

```

lspci

```

You will need these tools to install the nvidia drivers:

```

sudo apt-get install build-essential dh-make debconf debhelper xorg-dev

```

These tools contain things that help the nVIDIA drivers install the drivers to your system.

Reboot your machine from command line by running this command in command line:

```

sudo telint 6

```

If you need any more assistance, let me know.

---

### Post by lozzy on 2009-03-12
> **Neo_The_User said:**
> OK Go to Applications > Accessories > Terminal and type in this:

```

sudo /etc/init.d/gdm stop

```

Now this will make your screen all black with white text which is called "command line" also referred to as cli.

Now type this in when you get into command line.
```

links http://www.nvidia.com/Download/index.aspx?lang=en-us

```

Another way you could download the drivers is to download the drivers graphically using a program called firefox. This will make things easier. After you downloaded the drivers, save the drivers to your hard drive. Your hard drive consists of blocks of memory of which data is stored to. Save the drivers to your home folder. It should be in /home/lozzy or something like that.

Select your driver and follow the instructions in the driver page after choosing what graphics card you have. Check inside your computer to find out or run lspci from command line.

```

lspci

```

You will need these tools to install the nvidia drivers:

```

sudo apt-get install build-essential dh-make debconf debhelper xorg-dev

```

These tools contain things that help the nVIDIA drivers install the drivers to your system.

Reboot your machine from command line by running this command in command line:

```

sudo telint 6

```

If you need any more assistance, let me know.

OMG why is it so complicated??? i typed sudo /etc/init.d/gdm stop and pressed enter.. it asked for password but it wont let me type anything???

---

### Post by Neo_The_User on 2009-03-12
> **lozzy said:**
> OMG why is it so complicated??? i typed sudo /etc/init.d/gdm stop and pressed enter.. it asked for password but it wont let me type anything???

Just enter your password. The reason why it doesn't show up is because it is a "shadow password." You can google shadow passwords on google. What it does is it makes your password appear to be invisible on the screen.

---

### Post by philinux on 2009-03-12
Before anyone else chimes in lets find out which card the OP has.

Use this command. Make sure you copy and paste it in.

```
lspci | grep VGA
```

The capitals are needed.

---

### Post by Neo_The_User on 2009-03-12
> **philinux said:**
> Before anyone else chimes in lets find out which card the OP has.

Use this command. Make sure you copy and paste it in.

```
lspci | grep VGA
```

The capitals are needed.

Thank god you chimed in. hahaha!

---

### Post by lozzy on 2009-03-14
> **philinux said:**
> Before anyone else chimes in lets find out which card the OP has.

Use this command. Make sure you copy and paste it in.

```
lspci | grep VGA
```

The capitals are needed.

this is what came up when i did what u said ......

 Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

