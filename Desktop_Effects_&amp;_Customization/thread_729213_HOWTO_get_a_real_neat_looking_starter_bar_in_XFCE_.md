---
title: "HOWTO get a real neat looking starter bar in XFCE (and other wm´s)"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by Stefan_xfce on 2008-03-19
Hi,

I´m not a native speaker of English, so you might excuse me if I should express myself a bit funny once in a while.. :)

I´ve seen many screenshots of desktops with these Mac OS like starter bars on them lately and I wondered how to do this in XFCE, so I started to look in Google and figured it out.

I used "adesklets" and it works kind of fine for me, so if you should be unhappy with AWN for some reason, you should give this a try.

This is how my current desktop looks like:

[[IMG]http://img37.picoodle.com/img/img37/4/3/19/t_20080319211m_876ef6b.png[/IMG]](http://www.picoodle.com/view.php?img=/4/3/19/f_20080319211m_876ef6b.png&srv=img37)
Large pic:
[URL="http://img37.picoodle.com/img/img37/4/3/19/f_20080319211m_876ef6b.png"]http://img37.picoodle.com/img/img37/4/3/19/f_20080319211m_876ef6b.png
[/URL]

Neat, huh?
The firefox icon is enlarged, because the mouse has moved over it, also the other icons enlarge as soon as the mouse gets over them.

So, this is how I did it, step by step:

1. Install adesklets. It´s easily done using apt-get:
```
sudo apt-get install adesklets
```

If it shouldn´t work, you might have to switch on additional repositories in "Settings/Software Sources". If you select the first 4 entries on the first tab, it should work.

2. Download yap, the actual desklet. Go to 
[http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)
klick on "Desklets", scroll down to "yab" and download it. Open your file-manager, probably "Thunar", go to your home directory, or wherever you downloaded to, right click the file and choose "extract here".

3. Copy this new folder "yab 0.0.2" to ~/.desklets

4. Open a terminal. Type
```
cd ~/.desklets/yab-0.0.2/
./yab.py
```

then choose "r" for register and press Enter.

5. Now type
```
adesklets --xfce4
```
If you should use another desktop, like gnome or whatever, use adesklets --help to find the right switch for your one.

6. Now you should see the bar running with some not so great looking icons in the top left corner of your screen. Just leave it there for a while

7. Now you download my yab configurations and the icons I used from this free file hosting site:

[yab-0.0.2_custom.tar - 0.17MB](http://www.zshare.net/download/9190253eb27974/)

Click on "download now", close the occasional popup window, if an additional add should appear click "skip this add" on the top of the page, wait for the countdown to finish and download the file.

Go to your download folder, right-click the file yab-0.0.2_custom.tar and select "extract here"

In the new folder you will find the icons I used plus the config file I used.

If you like the icons, you can download the full set from deviant-art, it´s free for personal use:

[http://vicing.deviantart.com/art/rounder-png-65215412]("http://vicing.deviantart.com/art/rounder-png-65215412")
[http://vicing.deviantart.com/art/RONDer-2-66259044]("http://vicing.deviantart.com/art/RONDer-2-66259044")

If you use them regularly, you should be so kind to say at least thank you to the artist who put many hours of work in making them.

If you like these roundish icons, here´s another artist, who made similar ones:
[http://deleket.deviantart.com/gallery/#_featured]("http://deleket.deviantart.com/gallery/#_featured")

8. Now you replace the file ~/.desklets/yab-0.0.2/config.txt  with the my config file you just downloaded.
(You might want to make a backup copy of the original file, because you might prefer some settings of that one, e.g. I made a setting that the text above the icons only appears after a long while, whereas the original config makes it appear immediately).

Also you replace the folder
~/.desklets/yab-0.0.2/icons/   with the "icons" folder you downloaded

9. Now mimimize all windows and look at the actual running desklet in the top right corner of the screen. Right-click it and choose "restart". Wait about 10 seconds. A new bar with "my" icons should appear.
Right-click the bar again and choose "move". Move it to the place where you want it to be.

10. Of course you would want to personalize the bar with the apps you want. Therefore type 
```
mousepad ~/.desklets/yab-0.0.2/config.txt &
```
in a terminal

The config file opens. The last about 25 lines are the actual configuration. Here I explain some of the items:

'bar_opacity_1'   -  the higher the value, the less transparent the background bar becomes. If you change the value, you can always right-click the bar and "restart" to try out the new setting. If it doesn´t start again, you messed up the config file and you have to undo your last change.

 'caption_delay'   -   How many seconds do you want to wait until the text above the icon appears.

 'icon_max_height', widht, also min_height, etc.   -   Here you can determine how large the icons are zoomed in as well as normally.

'icon_spacing'   -   Here you can change the distance between the icons on the bar.

Ok, now for the important part:
'icons'   -   Here you can set up what icons should be used and what applications should be started when an icon is clicked.
The syntax is easy:

```
 [('folder.png', 'Thunar', 'thunar'),
```
folder.png   -   is the name of the png-icon file in the folder icons
Thunar   -   is the text that will appear over the icon when selected
thunar   -   is what will be executed, when the icon is clicked

If you want to make your own icon for e.g. xmms, you look for a nice icon for that, and you make an entry like that
 [('xmms.png', 'Xmms', 'xmms'),

You have to be precise about everything here, because if "adesklet" doesn´t find an icon file because you misspelled maybe, the whole thing won´t start.

11. If you made changes and you want to try them out, always "restart" as before.

12. Note: When I was new to this software I messed up things a couple of times and adesklets didn´t restart properly.
When you have to do the process I described here again to make it work again, you might notice that your config file is changed automatically when you register "yab" as a desklet again. You have to delete the automatically made entries in the config file then.

13. Ok, once you´re done you have a  cool starter bar now and you might want to start it every time you log in to X.
Therefore, go to "Settings/automatically started applications" (or something in that style, I have the German version and don´t know the exact English name), click on "add", and add the entry
```
adesklets --xfce4
```

14. If you want to see if it works properly, log out and log in again, and there it is, your cool new starter bar.
---
I hope someone finds this useful and I would be curious, what your desktops look like using this. So I would be pleased to see some screenshot of yours!

Cheers,
 Stefan

---

