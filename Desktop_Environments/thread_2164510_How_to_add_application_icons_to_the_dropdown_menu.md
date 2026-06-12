---
title: "How to add application icons to the dropdown menu?"
date: 2013-07-31
forum: Desktop Environments
---

### Post by 7nQecEL on 2013-07-31
[COLOR=#333333][FONT=UbuntuRegular]I'm trying to figure out how to add a category "Development" and sub-icons within that category. I know that sounds very confusing but please take a look at the link.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://i44.tinypic.com/2vwvk9j.png](http://i44.tinypic.com/2vwvk9j.png)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Awhile back, someone set up PyCharm and a "Development" category appeared, and when I hovered over it, it would show PyCharm, Postgres, Sublime Text, etc[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Unfortunately, I don't remember how it was done.. Right now I'm trying to set it up like that for my laptop.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]If anyone is familiar with what I'm talking about and can help, that'd be great![/FONT][/COLOR]

---

### Post by Dennis N on 2013-07-31
Try this in Xubuntu:

Right Click on Main (Applications) Menu Button.
Select Properties, and you get the Applications Menu Dialog.
Click on Edit Menu opens another dialog.
On the right side of this window, click on 'New Menu'
Enter information into the dialog which appears.
This creates a new Menu (category) in the list on the left.

You can then select the new category and add items to it with 'New Item'

---

### Post by Buntu Bunny on 2013-07-31
Do you have PyCharm installed on your laptop? Or any developer tools from the software center? If the Development Submenu doesn't already exist, it will be added when you install any of those tools. If you just want an empty development submenu, then follow Dennis N's instructions.

---

### Post by 7nQecEL on 2013-08-02
> **Buntu Bunny said:**
> Do you have PyCharm installed on your laptop?
I think I do.. I'm still quite new to linux (just recently started using it for internship and school) and the only instructions I've found for installing are these:

```

tar -xvzf [name of the tar.gz]
cd /bin
./pycharm.sh

```

Since the Development Submenu isn't showing up, I'm guessing this is wrong?

---

### Post by Buntu Bunny on 2013-08-02
7nQecEL, one thing about the Ubuntu Forums is that the folks here are always willing to help. 

I didn't see Pycharm in either the Ubuntu Software Center or Synaptic Package Manager. I did find installation instructions for Ubuntu 12.04 [here]("http://nourlcn.ownlinux.net/2012/10/install-pycharm-and-jdk-on-ubuntu-1204.html"). 

And here is a video that might be helpful: [Ubuntu Install applications packaged in tar.gz]("https://www.youtube.com/watch?v=Hl6qvn63rfs")

---

### Post by slickymaster on 2013-08-02
You can also achieve it by navigating to Applications Menu -> Settings Manager. Once the Settings dialogue window is opened, click the Main Menu icon and you'll be presented with the Main Menu dialogue window and in the left panel you should have the Development category listed between Accessories and Education categories. If not just click the 'New Menu' button and create it.

---

### Post by 7nQecEL on 2013-08-12
Ah yes thank you all for your help!

---

