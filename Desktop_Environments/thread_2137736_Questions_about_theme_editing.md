---
title: "Questions about theme editing"
date: 2013-04-21
forum: Desktop Environments
---

### Post by NBPX on 2013-04-21
I got tired of waiting for a tool for customizing themes for Ubuntu and can not stand looking at that annoying orange with a black eye. So I decided to get my hands dirty and create my own theme.


To do this I decided to change the theme Ambience. My questions are as follows.


Some images that make up the theme, such as the buttons of the windows are indexed images and not RGB images. To facilitate editing turned all images in RGB images. The system continues to run and I did not notice any problem arising from this change. Is there any reason for them to be indexed?


The images in my installation are the same ones in any installation of Ubuntu, ie, a computer screen with a higher density will use the same images tha a computer with a lower screen density? In other words, the theme will work on all computers?


Is there a vector version of these images?


The files that make up the themes change how often? How do I monitor and being informed of the changes in the files of the themes? If I create a modification and, say, an update of the system brings a new version of the theme I will have a problem? These themes work with different versions of Ubuntu?


Is there any tool or tutorial that facilitates the editing of these themes?

---

### Post by vasa1 on 2013-04-22
> **NBPX said:**
> ... So I decided to get my hands dirty and create my own theme.

To do this I decided to change the theme Ambience. My questions are as follows.
...
The files that make up the themes change how often? How do I monitor and being informed of the changes in the files of the themes? If I create a modification and, say, an update of the system brings a new version of the theme I will have a problem? These themes work with different versions of Ubuntu?

Is there any tool or tutorial that facilitates the editing of these themes?

Ambiance is part of the light-themes package. To monitor progress you could look at [https://launchpad.net/ubuntu/+source/light-themes](https://launchpad.net/ubuntu/+source/light-themes).

Re. modifications you make, if you make them in /usr/share/themes, they will be lost after each update. If you make them in ~/.themes, they'll be unaffected but the downside is that the themes in ~/.themes won't get any improvements if that's what an update brings.

I don't know anything at all about indexed images!

---

