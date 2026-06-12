---
title: "E:Couldn't find package"
date: 2010-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hongpan1986 on 2010-08-10
First of all, I'm an absolute noobie in ubuntu or linux, but I've been reading articles about linux for a few days now, and I've used windows for a few years. If I say something that you think is stupid, please bear with me. I really need help here.
 
So, I decided to multi-boot windows and ubuntu for my new studio 1458, cheapest hardware availabe from Dell. Thanks to a guy here who happens to have the same system shared his installation nightmare, I was able to install ubuntu without any problems.
 
After I boot into ubuntu, the first problem I ran into was that the WLAN card isn't working. So I searched and read a few articles, finally find out that this "wireless_tools.tar.gz" is supposed to help with the problem. When I tried to install this package, there is always an error message: " E: couldn't find package wireless-tools.tar.gz". It didn't matter what name I used, the same message appeared. I used "dir" to show this package is under the same directory, even copy its name and use "sudo apt-get install wireless-tools.tar.gz", I still got the same message. I tried to move the package to home directory; it won' work.
 
Please help, Thank you, people. I guess I need to learn how to install a package first.

---

### Post by Drenriza on 2010-08-10
Change directory to where the wireless-tools file is.
use
```
tar -xvfz wireless-tools.tar.gz
```
For extracting the file. Once extracted it can be installed.
Their is probably a README file. Open that file with vim for installation instructions.

---

### Post by Perfect Storm on 2010-08-10
Hi, welcome to the forums :)


To your questions;

You can't use apt-get on tar.gz files. apt-get you use to get stuff from ubuntu repositories (same way you use Ubuntu Software Center or Synaptic Package Manager).
A tar.gz is a compressed package which can contain everything, it's like a .zip file.
Right click ---> uncompress should unpack it.

wireless tools are in ubuntu repositories, simple search for it in synaptic Package Manager or install it via the terminal;

```
sudo apt-get install wireless-tools
```
(requires internet connection).

---

### Post by hongpan1986 on 2010-08-10
damn, I knew it's a newbie question. I didn't know tar.gz is like zip file in windows. Thank you, people. You are the best.

---

### Post by hongpan1986 on 2010-08-11
> **Artificial Intelligence said:**
> Hi, welcome to the forums :)


To your questions;

You can't use apt-get on tar.gz files. apt-get you use to get stuff from ubuntu repositories (same way you use Ubuntu Software Center or Synaptic Package Manager).
A tar.gz is a compressed package which can contain everything, it's like a .zip file.
Right click ---> uncompress should unpack it.

wireless tools are in ubuntu repositories, simple search for it in synaptic Package Manager or install it via the terminal;

```
sudo apt-get install wireless-tools
```(requires internet connection).

What if I don't have a internet connection? What I do after I unpack it? it's nothing like windows, just click and click. I got my wireless working already, just wanna know how to install a downloaded package, like the one here, what should I do after I unpack it?

Thank you for the help

---

### Post by hongpan1986 on 2010-08-11
Never mind, the first guy just answer the question.

Thank you, people.

---

