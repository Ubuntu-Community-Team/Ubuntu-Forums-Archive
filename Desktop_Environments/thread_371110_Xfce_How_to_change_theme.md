---
title: "Xfce: How to change theme"
date: 2007-02-26
forum: Desktop Environments
---

### Post by alan2 on 2007-02-26
Hello,

I have been desperately trying to install a theme ([http://www.deviantart.com/deviation/49478473/](http://www.deviantart.com/deviation/49478473/)) which requires rezlooks, which I got from here: [http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb](http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb)

So I installed it without any problems and then extracted the theme to /usr/share/themes. But it still doesn't show up in "User Interface Settings". Restart didn't help, as well as copying the theme to ~/.themes

Im new to Xfce so I would appreciate some help with this :)


Alan

---

### Post by crimesaucer on 2007-03-06
I use xubuntu edgy, and had similar problems with every theme I tried to install from xfce-looks. I followed instructions correctly, extracted them and tried to put them into /.themes and /usr/share/themes and they still would not show up. Then I gave up for a while.

So after just using the extra themes available in Synaptic for a few months, I decided I would just learn how to write my own theme for xfce.

Here is a link to a "How To" modify your xfce-engines gtkrc that I wrote: [http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)

There are some pictures on there to show how you can (IMO) improve your current xubuntu themes by just modifying one of your gtkrc files located in you /usr/share/themes/Xfce-theme_name/gtk-2.0/gtkrc

I used the theme Xfce-winter.

All you need to do is goto terminal, and change directory to you /usr/share/themes/

```
cd /usr/share/themes
```

then...

```
ls
```

to list the themes you have installed.

Then (while you are still in the theme directory) pick one and copy it to your home folder. Let's use Xfce-winter for example.

```
cp -r Xfce-winter ~/
```

the -r will cp it and all of it's directories in it.

then goto your homefolder, open your Xfce-winter folder then open the gtk-2.0 folder, and then click onto the gtkrc and open it with mousepad.

Then use my "How To" to know where to modify your gtkrc.

When you're done, change the name to something like Xfce-winter_2

and then move it back into your /usr/share/themes with this code

```
sudo mv Xfce-winter_2 /usr/share/themes
```

then open your User Interface Preferences and you will see it underneath your original Xfce-winter.

I have almost 20 personal themes that I have added using this method.

Here is a picture of a theme that I have posted on that site for anyone to use or change to their liking:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-40-4.png[/IMG]

Have fun, and always give credit where credit is due if you share a theme that you modified from someone else.

---

