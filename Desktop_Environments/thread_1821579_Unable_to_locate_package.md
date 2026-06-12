---
title: "Unable to locate package"
date: 2011-08-09
forum: Desktop Environments
---

### Post by WarSpanner on 2011-08-09
Hello,

I'm trying to install Ruby on Rails on an Ubuntu desktop VM. The network connection works ok but I can't seem to get this to work:

sudo apt-get install ruby1.9.2

I want the latest version of Ruby.

Is this because I haven't enabled some repository or something - I dimly recall having to 'enable universe' before now... but can't remember why or how....

Thanks in advance.

---

### Post by ~!geek!~ on 2011-08-09
Open synaptic or some other package manager. Search for ruby in it. 
In ubuntu 11.04, latest available ruby package is ruby1.9.1 with ruby1.8 being kindaa recommended one. 
So either use package manager or 
if you are using ubuntu 11.04 (I don't remember the verion of ruby available in previous ubuntu repository)

> sudo apt-get install ruby1.9.1

(Preferred way is to use package manager. You can select other ruby packages like dev ones )

If you want latest version of ruby, try to search for official ppa for ruby (sorry for not providing ppa name)

---

### Post by WarSpanner on 2011-08-09
When I did that I only saw 1.8. I suppose I could use 1.8 but I'd rather use 1.9.2. 1.9.1 isn't supported by Rails. 1.8 is a bit old now.

EDIT : Can't seem to find a PPA that looks 'trustworthy' and has 1.9.2, ah well guess it's back to 1.8 then.

Thanks.

---

### Post by WarSpanner on 2011-08-09
Ah, seems rvm is the solution. It seems to recompile ruby from source each time and you can keep your ruby and rails versions separate and switch between them - cool.

managed to get 1.9.2 installed and working. :guitar:

---

