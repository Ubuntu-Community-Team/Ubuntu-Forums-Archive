---
title: "How to install a list of packages from a text file"
date: 2012-03-19
forum: Desktop Environments
---

### Post by marinara on 2012-03-19
Everyone knows that it's easy to install Lubuntu on a new PC.  
Did you also know that it's easy to take a list of packages and install them automatically?

I based this post loosely on [this.]("http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html")

open terminal (of course)
assuming you have a file named packages.txt that looks like this:
```
firefox
vim-gtk
guake
xchat-gnome
vlc
ispell
wordnet
rar
 unrar
htop
```text file needs to list exactly one package per line, and no extra lines!

now in the terminal, execute the following 4 lines individually: (note the parens)
```

sudo su
apt-get install dselect 
while read line;do echo -en "$line install\n"; done <packages.txt|dpkg --set-selections
dselect 
```(type i at the prompt)

And it starts!

what I did, was every time I installed a package, i added a line to a text file named 'packages.txt'
So, I'm not installing anything not listed in the packages.txt file
Enjoy!

another way [here ]("http://users.telenet.be/mydotcom/howto/linux/automatic.htm")

---

### Post by marinara on 2012-04-06
ok in the above, packages.txt is the name of the package listing.  you will need to run dselect  after you read the file with the bash script.
type i to install and wait

---

### Post by markbl on 2012-04-06
This is much easier.
```

sudo xargs -a packages.txt apt-get install

```

---

### Post by gastly on 2012-04-07
An easier way is to make your text file like this:

> 
firefox         install
vim-gtk         install
clementine      install
cowsay          install


and then do:

> 
sudo dpkg --set-selections < packages.txt
sudo apt-get -u dselect-upgrade


The advantage is that it allows you to remove packages as well, so you can replace install next to a package name with **purge** and it will remove that package. Also, there's no need to install the dselect package with this method.

Cheers :)

---

