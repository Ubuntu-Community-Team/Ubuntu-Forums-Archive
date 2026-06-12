---
title: "Please help me install an engine!"
date: 2010-04-09
forum: Desktop Environments
---

### Post by dannylee094 on 2010-04-09
Hi

First of all I am new to ubuntu, and so far I'm hating it.

I wan't to install an engine to get this theme: 

[http://gnome-look.org/content/show.php/Equinox+GTK+Engine?content=121881](http://gnome-look.org/content/show.php/Equinox+GTK+Engine?content=121881)

I don't understand, before you use technical terms;

[B] GTK+ library development files (*libgtk2.0-dev* on Debian/Ubuntu, *gtk2-devel* on Fedora) with your favourite package manager. 

Then to compile the Equinox engine, extract the corresponding archive in [your home]("http://gnome-look.org/content/show.php/Equinox+GTK+Engine?content=121881#") folder. In the new directory, run the following commands: 
./configure --prefix=/usr --enable-animation

make

On Fedora 64 bits (and perhaps other distribs), compilation don't work with the options above. You must run:
./configure --prefix=/usr --libdir=/usr/lib64 --enable-animation

Finally, run this command as root: 
make install

[/B]
I just want to get this nice theme installed and then I can go. I don't understand what compiling is so please can you explain that

I don't know how to reward anyone that helps, apart from saying thanks very  much.

Danny!

---

### Post by steveneddy on 2010-04-09
Here's the link to a .deb file

Download it and double click to install

[http://gnome-look.org/content/show.php/Equinox+Ubuntu+Packages?content=121882](http://gnome-look.org/content/show.php/Equinox+Ubuntu+Packages?content=121882)

EDIT:

It will come in a .tar.gz format - just DL it to your desktop, right click and select "Extract Here" - open the folder it creates and follow the instructions on the provided link.

---

### Post by dannylee094 on 2010-04-10
Great, I'm Really happy with that, thanks!

One theme though that I would love is this:

[http://gnome-look.org/content/show.php/Soffice?content=67854](http://gnome-look.org/content/show.php/Soffice?content=67854)

Can anyone say an easy way for me to install that aurora engine?

thanks!

---

### Post by steveneddy on 2010-04-10
> **dannylee094 said:**
> Great, I'm Really happy with that, thanks!

One theme though that I would love is this:

[http://gnome-look.org/content/show.php/Soffice?content=67854](http://gnome-look.org/content/show.php/Soffice?content=67854)

Can anyone say an easy way for me to install that aurora engine?

thanks!

A little research on your part would help you quite a bit.

I realize you are new to Ubuntu, but if you start looking in Synaptic Package Manager you may find most of what you are looking for in the future. Just friendly advice, not preaching. If you have issues, don't hesitate to post a thread or **search the forums**.

Aurora should be in the repos - look under gtk2 listings.

```
sudo apt-get install gtk2-engines-aurora
```

if you don't find it right away, just add more Ubuntu sources by opening the Software Sources manager by going to

System --> Administration --> Software Sources

and check off the boxes for universe, multiverse and restricted.

when you close the window it will ask you to reload the list, simply click yes.

then try the command above again and it should work.

EDIT:

Follow the link in my sig that corresponds to the version of Ubuntu you are using. You will find a lot of useful info there for new users.

Also the [Ubuntu Resources]("http://www.psychocats.net/ubuntu/index.php") link will show you even more info that you may find interesting.

---

