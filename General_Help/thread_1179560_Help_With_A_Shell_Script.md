---
title: "Help With A Shell Script?"
date: 2009-06-05
forum: General Help
---

### Post by jlacroix on 2009-06-05
Hello again!

I have created a shell script that I use to install programs and copy files to various places. What I decided to do was create some text that pauses the script and wants me to press a key to continue. Unfortunately, what I have done does not work. Here is an excerpt from my shell script so you can see what I am dealing with (this is not the whole thing):

```
read -p "Press any key to create the required directories…"
mkdir /home/jeremy/.mame
mkdir /home/jeremy/.mame/roms
mkdir /home/jeremy/Shared
mkdir /home/jeremy/.unison

read -p "Press any key to add the Virtualbox GPG key…"
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

read -p "Press any key to add the PlayonLinux respository"
sudo wget http://deb.playonlinux.com/playonlinux_jaunty.list -O /etc/apt/sources.list.d/playonlinux.list

read -p "Press any key to add the Virtualbox repository…"
echo "deb http://download.virtualbox.org/virtualbox/debian intrepid non-free" | sudo tee -a /etc/apt/sources.list

read -p "Press any key to add the Medibuntu repository..."
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

read -p "Press any key to update the package sources…"
sudo apt-get update 
```

What happens is that the script bypasses the "press any key" text and executes the next line even though I didn't press any key.

---

### Post by kaibob on 2009-06-05
Try this:

```
read -n 1 -p "Press any key to continue."
```

From the man page:

> -n nchars. read returns after reading nchars characters rather than waiting for a complete line of input.

If the script still does not pause, you may want to include a variable at the end of the read line, as it appears to be required by some versions of read.

---

### Post by jlacroix on 2009-06-05
> **kaibob said:**
> Try this:

```
read -n 1 -p "Press any key to continue."
```

From the man page:

No such luck:

```
read: 1: Illegal option -n

```

---

### Post by unutbu on 2009-06-05
read is expecting another argument, the variable in which the response is stored:

```
read -p "Press any key to create the required directories&#8230;" arg
echo "You just typed $arg"

```
```

% test.sh
Press any key to create the required directories&#8230;blah
You just typed blah
```

---

### Post by jlacroix on 2009-06-05
Message removed.

---

### Post by jlacroix on 2009-06-05
> **unutbu said:**
> read is expecting another argument, the variable in which the response is stored:

```
read -p "Press any key to create the required directories…" arg
echo "You just typed $arg"

```
```

% test.sh
Press any key to create the required directories…blah
You just typed blah
```

So do I just use "arg" over and over again, or do I need a new variable each time?

---

### Post by unutbu on 2009-06-05
Using arg repeatedly would work :)

---

### Post by jlacroix on 2009-06-05
> **unutbu said:**
> Using arg repeatedly would work :)

Worked like a charm! Where did that thanks button go?

---

### Post by unutbu on 2009-06-05
I'm glad it worked for you :)
The thanks button went to bit-bucket heaven martyred in the name of server stability.

---

### Post by kaibob on 2009-06-05
> **jlacroix said:**
> No such luck:

```
read: 1: Illegal option -n

```

Sorry! I incorrectly assumed you were using bash.

---

