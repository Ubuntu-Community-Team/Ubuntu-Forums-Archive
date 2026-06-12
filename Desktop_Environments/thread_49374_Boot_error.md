---
title: "Boot error"
date: 2005-07-16
forum: Desktop Environments
---

### Post by t2kburl on 2005-07-16
During the boot process I get an error message

t_kernel_font -- Invalid Argument                       [fail]

it finishes booting afterwards and everything seems to run OK, but I'd like to make it go away so my splashy screen stays up

---

### Post by demonicbunny on 2005-08-05
Do you use Splashy? 

If so you might want to check out the splashy faq at [Splashy FAQ](http://clickfanatic.l2p.net/splashy/wiki/index.php?title=Main_Page) 

In case you can't be bothered or the page is unavailable here's the info regarding the t_kernel_font error :-

 > At about 70-80% of booting process Splashy goes to verbose mode and shows:

 t_kernel_font: Invalid Argument

It's a bug related with the /etc/init.d/console-screen.sh file that does not set the font for framebuffer properly, this bug is unsolved. The work around is to edit the config.xml and set:

 "autoverboseonerror" to "no"


---

### Post by teddy69 on 2005-10-31
[QUOTE=t2kburl]During the boot process I get an error message

t_kernel_font -- Invalid Argument                       [fail]

it finishes booting afterwards and everything seems to run OK, but I'd like to make it go away so my splashy screen stays up[/QUOTE]

I myself just found the answer to this so thought I'd share, so as mentioned above just do what the faq says, I had trouble locating the config.xml file so here's where it's located:

```
/etc/upower/global-config.xml
```

and change autoverbosemode to no:

```
<AutoverboseOnError>no</AutoverboseOnError>
```

---

