---
title: "How to make ubuntu 8.10 look like windows vista."
date: 2009-04-03
forum: Desktop Environments
---

### Post by stukpixel on 2009-04-03
I think the guides seen here:
[http://gnome-look.org/content/show.php/Aero-clone?content=57352&PHPSESSID=b9a68871d79ab7ec599715ed249c07d9](http://gnome-look.org/content/show.php/Aero-clone?content=57352&PHPSESSID=b9a68871d79ab7ec599715ed249c07d9)
and here:
[http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html](http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html)

...are both outdated. since when I tried imstalling the theme that the guides specifies in the default theme manager it said the gtk+ engine was not installed, and it didn't even use the segoe ui fonts I already installed.

I tried installing the screenlet using the included sh, but that didn't work.

also I deleted the vista theme which then led to upon a reinstall, say "cannot move directory over directory"

---

### Post by Mason Whitaker on 2009-04-03
...Why would you want to? Vista is bleh

---

### Post by stukpixel on 2009-04-03
> **Mason Whitaker said:**
> ...Why would you want to? Vista is bleh

everyone has their reasons. I just prefer the look of vista- obviously.

I just looked at the ubuntu code of conduct, but, amazingly, an unhelpful reply such as yours in a help thread is not forbidden.

---

### Post by UbuntuNerd on 2009-04-03
for the problem you can't move directory over directory you have to go to your home folder and press Ctrl+H to show the hidden folders, and go to 
```
/usr/share/themes
```
and delete the folder of the theme, and then install it again, make sure to do it immediately or it won't work.
 also you can use the themes from this [guide](http://my.opera.com/ubuntunerd1/blog/make-ubuntu-look-like-windows-vista)
I made it myself and I know they work.

---

### Post by Giblet5 on 2009-04-03
> **stukpixel said:**
> everyone has their reasons. I just prefer the look of vista- obviously.

I just looked at the ubuntu code of conduct, but, amazingly, an unhelpful reply such as yours in a help thread is not forbidden.


You actually looked it up over an opinion?

Wow... I see why you want a Vista theme.

Are you after the whole shebang, or just the window decorations? Emerald's "Vista-Look" theme replicates the decorations, even to the pulsing red close gadget.

For the whole shebang, you can get a perfect theme [here]("http://www.amazon.com/Windows-Vista-Ultimate-with-SP1/dp/B0013O77GM/ref=pd_bbs_sr_3?ie=UTF8&s=software&qid=1238795229&sr=8-3") for $249.99.

---

### Post by stukpixel on 2009-04-03
Giblet5: further sarcasm and irrelevant comments will be ignored as this is not the appropriate board for such.

UbuntuNerd: Thank you very much for this guide, and your suggestion to delete the aero folder from my theme folder, but is there anything will simulate the start button/orb?

---

### Post by Giblet5 on 2009-04-03
> **stukpixel said:**
> Giblet5: further sarcasm and irrelevant comments will be ignored as this is not the appropriate board for such.

Do what you do well, I guess.


> UbuntuNerd: Thank you very much for this guide, and your suggestion to delete the aero folder from my theme folder, but is there anything will simulate the start button/orb?

You're out of luck there. The closest you'll get is KDE4 with the Vista panel theme. You'll have to steal M$ icons to finish the effect, but you're on your own in that regard as it violates Microsoft's rights to use their icons except as licensed. See the EULA for Vista.

I haven't seen a KDE theme that accurately replicates the window decorations, but I haven't looked lately.

---

### Post by SunnyRabbiera on 2009-04-03
> **stukpixel said:**
> Giblet5: further sarcasm and irrelevant comments will be ignored as this is not the appropriate board for such.

UbuntuNerd: Thank you very much for this guide, and your suggestion to delete the aero folder from my theme folder, but is there anything will simulate the start button/orb?

Gnomenu is close.
But seriously Ubuntu is not intended to look like Vista, act like Vista, or be like Vista.
Really you are asking for sarcastic replies by expecting an exact duplicate of Vista and by saying you prefer its look.
Ubuntu has its interface, Vista has its interface, the two are night and day when concerning looks and interface.
Ubuntu usually aims for a simplistic look, both friendly, functional and good on resources.
Vista aims for the fancy interface crowd who buys a Mac for its pretty looks and is quite shaky and way too heavy on memory for my tastes.
The goal of the new linux user in my opinion is not to expect vista, if you want vista then use vista and try not to expect perfection from a OS that is as far from vista as one can possibly get.

---

### Post by stukpixel on 2009-04-03
if you took a look at this thread's title, I simply said, "look like" not "look exact". But really I should just ignore your entire post, though I thank you for the gnomenu.

If this is a support board with moderation that enforces its own rules, then I imagine I shouldn't be "asking" for anyone to state their opinions. 

This is not a discussion, its help and help only.
 
"Vista aims for the fancy interface crowd who buys a Mac for its pretty looks and is quite shaky and way too heavy on memory for my tastes." This is a sentence that needs to be refined, or redone. 

But please don't do it in this thread :).

How would  I go about getting a start menu/removing the top panel (gnomenu wasn't as functional as windows), and also installing an icon pack (such as nuoveXT-aero)?

---

### Post by UbuntuNerd on 2009-04-03
> **stukpixel said:**
> if you took a look at this thread's title, I simply said, "look like" not "look exact". But really I should just ignore your entire post, though I thank you for the gnomenu.

If this is a support board with moderation that enforces its own rules, then I imagine I shouldn't be "asking" for anyone to state their opinions. 

This is not a discussion, its help and help only.
 
"Vista aims for the fancy interface crowd who buys a Mac for its pretty looks and is quite shaky and way too heavy on memory for my tastes." This is a sentence that needs to be refined, or redone. 

But please don't do it in this thread :).

How would  I go about getting a start menu/removing the top panel (gnomenu wasn't as functional as windows), and also installing an icon pack (such as nuoveXT-aero)?

check [here](http://www.natewelch.com/index.php?name=News&file=article&sid=41) to make a custom (Ubuntu) Start Menu button but I haven't try it myself I like the way the menus are. you could just move everything from the top panel to the bottom just like it is on top or as icons.

To remove any panel just right click on it and deleted panel.

---

### Post by SunnyRabbiera on 2009-04-03
> **stukpixel said:**
> if you took a look at this thread's title, I simply said, "look like" not "look exact". But really I should just ignore your entire post, though I thank you for the gnomenu.

If this is a support board with moderation that enforces its own rules, then I imagine I shouldn't be "asking" for anyone to state their opinions. 

This is not a discussion, its help and help only.
 
"Vista aims for the fancy interface crowd who buys a Mac for its pretty looks and is quite shaky and way too heavy on memory for my tastes." This is a sentence that needs to be refined, or redone. 

But please don't do it in this thread :).

How would  I go about getting a start menu/removing the top panel (gnomenu wasn't as functional as windows), and also installing an icon pack (such as nuoveXT-aero)?

If you want to ignore people fine thats your priority, I am just saying that if you are going to expect the perfect Vista look a like you are in for one heck of a disappointment.
Look I am trying to be neutral no matter how badly I dislike vista (I have had constant issues with it, so have many windows users including my husband)
Gnomenu is not a perfect solution but it gets some of the job done for your demands, its still in development so its not going to replicate the vista menu exactly.
Installing icons should be simple, right click desktop and select "change wallpaper" and go to the "theme" tab
click the install button and select your icon pack.
NuoveXT-aero will come close to the vista icon theme, I use it off and on myself when I am bored.
But still the only way to get the total Vista look and feel is to use Vista, Ubuntu is not meant to be an exact clone nor will ever be an exact clone.

---

### Post by Giblet5 on 2009-04-03
> **stukpixel said:**
> if you took a look at this thread's title, I simply said, "look like" not "look exact". But really I should just ignore your entire post, though I thank you for the gnomenu.

If this is a support board with moderation that enforces its own rules, then I imagine I shouldn't be "asking" for anyone to state their opinions. 

This is not a discussion, its help and help only.

Most of the help on this forum is provided by volunteers, most of whom are professionals in DP or IT fields 40 hours/week, then they do this in their spare time out of a desire to add tangible value to the distribution and the Ubuntu community at large.

I keep things as professional and as accurate as I can. I have opinions, as do you. Yours was given in the thread topic, and in every post of yours, since.

If you want only professional help, and if you want the luxury of guiltlessly correcting those whom you have asked for help, there are no shortage of people and groups willing to sell it to you ie, you swap money for limited recourse.

As to the thread itself, **SunnyRabbiera** has provided the best and most accurate answer and your response was to correct the content.

You have been argumentative in every post.

**You started this thread so you could troll.**

---

### Post by andrea000 on 2009-04-04
Hello you may try this [link]("http://ishan-liyanage.blogspot.com/2006/10/vista-theme-on-ubuntu.html") or this [link]("http://gnome-look.org/content/show.php/Complete+Vista+Aero+theme+(automated)?content=72318") and here is another [link]("http://gnome-look.org/content/show.php/Windows+Vista+%2Bvista+aero+Full+pack?content=70428")
and yet another [link]("http://gnome-look.org/content/show.php/Linsta+Aero+Modified?content=71257") here i my self do 
not use these but i am not one to judge if you like the look 
go for it.

---

### Post by pg-13(prostitute) on 2009-04-04
vista is glam looking just to (flip)ing slow for my MP3 listening and painting with my wacom

linux is pretty bare-butted so i can paint and listen to songs without 1,000,000 peieces of trash slowing things down.

---

### Post by stukpixel on 2009-04-04
I wonder why people are choosing a help thread to express their opinions.

SunnyRabbier: I think you missed a step or two when describing how to install icons; am I/suppose to paste it into an icon folder of some sort? 

andrea000: thank you for the links- I will take a look into each one of them. EDIT: the first two don't work as intended but thanks again for the suggestion.

ubuntunerd: Ill consider that method as a last resort :).

does anyone know to install the orb screenlet by kimmick?

EDIT: Found this. 
It looks nice, but I need to modify it.
[http://www.gnome-look.org/content/show.php/Windows+Vista+Theme?content=101019](http://www.gnome-look.org/content/show.php/Windows+Vista+Theme?content=101019)

Also I am having trouble using gnomenu, can anyone help?

---

### Post by SunnyRabbiera on 2009-04-04
> **stukpixel said:**
> I wonder why people are choosing a help thread to express their opinions.

SunnyRabbier: I think you missed a step or two when describing how to install icons; am I/suppose to paste it into an icon folder of some sort? 

andrea000: thank you for the links- I will take a look into each one of them. EDIT: the first two don't work as intended but thanks again for the suggestion.

ubuntunerd: Ill consider that method as a last resort :).

does anyone know to install the orb screenlet by kimmick?

EDIT: Found this. 
It looks nice, but I need to modify it.
[http://www.gnome-look.org/content/show.php/Windows+Vista+Theme?content=101019](http://www.gnome-look.org/content/show.php/Windows+Vista+Theme?content=101019)

Also I am having trouble using gnomenu, can anyone help?

Gnomenu I really cant help too much with as I dont use it, but your icon set installation should be simple.
when you click on the install button make sure to go to the directory where you saved your file and when you find it hit the "open" button.
No need to copy and paste anything.
As for the Vista theme you have eh it looks not too customizable or even functional as a drop in vista like theme.
[http://gnome-look.org/content/show.php/Murrina-LiNsta+(LiNsta+is+Not+Vista+%3B-)?content=61068](http://gnome-look.org/content/show.php/Murrina-LiNsta+(LiNsta+is+Not+Vista+%3B-)?content=61068)

That theme is better in my opinion, its nice and clean and is quite good looking for a vista like theme

---

### Post by stukpixel on 2009-04-04
thank you for Linsta. though it doesn't look to well in minor ways (godforbid I change the firefox theme) I am now using it as my default theme.

How would I go about installing a new cursor pack for ubuntu?

---

### Post by JK3mp on 2009-04-04
Wow...you can't put the word Windows, (especially vista) in a linux forum and expect no debate. LoL *sorry pointless post*

---

### Post by hblaw on 2009-04-05
> **JK3mp said:**
> Wow...you can't put the word Windows, (especially vista) in a linux forum and expect no debate. LoL *sorry pointless post*

:) And the mere presence of these words is a provocation and some people need to justify their preference with the fact that they are volunteering their opinions rather than selling them.

---

### Post by pbpersson on 2009-04-05
> **stukpixel said:**
> 

Also I am having trouble using gnomenu, can anyone help?

What sort of error?

At what point?

Using what tutorial?

---

### Post by stukpixel on 2009-04-05
nevermind about gnomenu, I got it to work, but it was not too different from the normal gnome menu panel object.

I am still looking for a way to change its icon, as well as install a vista cursor theme pack.

---

### Post by UbuntuNerd on 2009-04-05
> **stukpixel said:**
> nevermind about gnomenu, I got it to work, but it was not too different from the normal gnome menu panel object.

I am still looking for a way to change its icon, as well as install a vista cursor theme pack.

stukpixel download the vista cursor theme from the guide I gave you is in there.

---

### Post by stukpixel on 2009-04-05
I did. Or rather, I tried.

Perhaps I'm doing it wrong, but aero-drop does not show up unders cursor option in customize. I have a wii cursor set installed to see if it was my method, but it works fine (switches between normal and wii for some reason).

---

### Post by UbuntuNerd on 2009-04-05
> **stukpixel said:**
> I did. Or rather, I tried.

Perhaps I'm doing it wrong, but aero-drop does not show up unders cursor option in customize. I have a wii cursor set installed to see if it was my method, but it works fine (switches between normal and wii for some reason).

how did you install it?

---

### Post by stukpixel on 2009-04-05
I copy-pasted it into the .icon folder. I want to appearance, themes, customize, cursors, and it was not there.

---

### Post by UbuntuNerd on 2009-04-06
that's one way, open the appearance preference box make sure you have (Theme) selected and drag the cursor folder to the appearance Preference box to install it, it should work

---

### Post by stukpixel on 2009-04-06
failed. cannot move a directory over a directory.

---

### Post by UbuntuNerd on 2009-04-06
if that happened it means you didn't remove the cursor folder you paste in  ".icon folder" from when you try installing it the first time. Try removing the folder and then install it by dragging it to the appearance box

---

### Post by stukpixel on 2009-04-06
it shows up, but in use, it only changes to the aero cursor when its on certain applications,for example firefox. Even then, it doesn't show the loading and it reverts to the old cursor,

EDIT: Apparently a reboot fixed that issue. Cursor pack works rather nicely. Now to find a vista svg orb to replace the gnome menu ubuntu svg...

---

### Post by UbuntuNerd on 2009-04-06
I was going to suggest to log out and log back in sometimes that helps.

---

### Post by UbuntuNerd on 2009-04-06
a while back I did the "Orb" myself. all you have to do is install the "orb" screenlet and place the orb screenlet above the main-menu button and lock the position in place 
you can also install the vista menu from [here](http://www.gnome-look.org/content/show.php/vistamenu(GnoMenu)?content=95756) also check [here](http://www.gnome-look.org/content/show.php/Black-Ubuntu-Orb+Start+Button?content=98703)

---

### Post by andrea000 on 2009-04-06
I was looking for something and came across a vista for gnome
and remembered i your post you can check out what i found [here]("http://www.gnome-look.org/content/show.php/Vista+Start+Menu+for+Gnome+Panel?content=71425")

---

### Post by hp owner on 2009-04-06
so you want it like this??

i have the menu like vista also, but couldn't get it to stay open

---

### Post by andrea000 on 2009-04-06
> **hp owner said:**
> so you want it like this??

i have the menu like vista also, but couldn't get it to stay open

check out the link i posted

---

### Post by stukpixel on 2009-04-06
> **andrea000 said:**
> I was looking for something and came across a vista for gnome
and remembered i your post you can check out what i found [here]("http://www.gnome-look.org/content/show.php/Vista+Start+Menu+for+Gnome+Panel?content=71425")

ah. that does not work for ubuntu 8.10.
I'm actually quite happy with the default gnome menu panel, just need find a way to change the icon to a vista orb.svg (which is impossible to get from .png as well as the internet)

---

### Post by andrea000 on 2009-04-06
oh well i tried and i was just thinking maybe you could it
but i will stop sending idea's your way since it can't be 
done.

---

### Post by stukpixel on 2009-04-07
actually, the author of the vista menu says "Does not work on ubuntu 8.10"

---

### Post by UbuntuNerd on 2009-04-07
> **stukpixel said:**
> ah. that does not work for ubuntu 8.10.
I'm actually quite happy with the default gnome menu panel, just need find a way to change the icon to a vista orb.svg (which is impossible to get from .png as well as the internet)

"stukpixel" look at this link it shows how to change the icon on the menu: [http://www.pendrivelinux.com/changing-the-ubuntu-start-menu-panel-icon/]("http://www.pendrivelinux.com/changing-the-ubuntu-start-menu-panel-icon/")

---

### Post by Hyper Tails on 2009-04-07
I made mine linux box look like vista once with a sidebar and all the same look (a ubuntu orb that is)

it was cool
If only i had a photo of it i would love to show it.

---

### Post by stukpixel on 2009-04-09
> **UbuntuNerd said:**
> "stukpixel" look at this link it shows how to change the icon on the menu: [http://www.pendrivelinux.com/changing-the-ubuntu-start-menu-panel-icon/]("http://www.pendrivelinux.com/changing-the-ubuntu-start-menu-panel-icon/")

I know how to replace it- but I need to find the vista orb first :S

---

### Post by UbuntuNerd on 2009-04-11
"Stukpixel" try this .svg vista logo.

---

### Post by stukpixel on 2009-04-11
it is very small when it is implemented on the panel bar, and the windows panes are all white.

---

### Post by UbuntuNerd on 2009-04-11
that's weird?

---

### Post by stukpixel on 2009-04-12
is it different for you?

---

