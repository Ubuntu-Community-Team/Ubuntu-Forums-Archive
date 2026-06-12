---
title: "What was the command line for that game?"
date: 2006-08-13
forum: Gaming &amp; Leisure
---

### Post by Steve S. on 2006-08-13
I have two sons, so I put a whole bunch of games on this computer from synaptic.

But a few of them didn't show up in applications>games, yet I can find an /etc file on them.

So, how do I figure out how to start that game in terminal?  Do I look back through synaptic for ideas, or is there a direct way/file to look in?  Or is there some other way to make sure they are put in applications>games?

---

### Post by Lord Illidan on 2006-08-13
> **Steve S. said:**
> I have two sons, so I put a whole bunch of games on this computer from synaptic.

But a few of them didn't show up in applications>games, yet I can find an /etc file on them.

So, how do I figure out how to start that game in terminal?  Do I look back through synaptic for ideas, or is there a direct way/file to look in?  Or is there some other way to make sure they are put in applications>games?

In synaptic, if you click on properties, they should have a /usr/bin or /etc file.

Generally, entering their name in a terminal should work.

---

### Post by foolsh on 2006-08-13
most games are installed to /usr/games

---

### Post by patrick295767 on 2006-08-13
try to install them the kicker bar
or gnome-panel
  
In kicker bar, they show up better usually.
  
I have same troubles too, and had to add manually the entries for dosbox gaming ... emulators ... 
rather long.
  
```
apt-get -f -y install kicker gnome-panel
```
  
Good luck !

---

### Post by Steve S. on 2006-08-13
Thanks for all the input, everyone.  I did find them in /usr/games and there were actually quite a few more than I thought.

So, how can I get those to be listed in the Applications>Games area?  Any way?

---

### Post by Steve S. on 2006-08-13
Whoa!  Just looking in /usr/games I ran "blast" (apparently a game I downloaded) and it turned my mouse/cursor into a gun and all I could do was shoot holes in everything on my desktop!:eek:  I couldn't even escape out of it...how do I shut that one down? :D  Crazy...had to turn the computer off.

Ok, seriously, I obviously have to have these games set into some kind of drop down box...the Applications one being the most obvious.  So, can someone tell me how to do that?  If not there, then what is the most efficient way to put them in another drop down box of some sort?  What would look best?

---

### Post by foolsh on 2006-08-13
if you use kubuntu install this application
```
sudo apt-get install kappfinder
```
it might still work with ubuntu's gnome desktop i dont know
then run kappfinder from the run command prompt or terminal
this will automate the process of adding menu items for program to the menu

---

### Post by Steve S. on 2006-08-13
> **foolsh said:**
> if you use kubuntu install this application
```
sudo apt-get install kappfinder
```
it might still work with ubuntu's gnome desktop i dont know
then run kappfinder from the run command prompt or terminal
this will automate the process of adding menu items for program to the menu

Excellent!  Thanks, I'll give it a shot...

---

### Post by Steve S. on 2006-08-13
> **Steve S. said:**
> Excellent!  Thanks, I'll give it a shot...

Yeah, it looks like I'll have to do something other than kappfinder, but thanks for the idea.   That seems to be something like what I am looking for.

But kappfinder looks for non-kde items to add to the menu...well, most of what I have is non-kde, even though much of it is already on the menu, and the kappfinder scan isn't what I'm looking for.

Other ideas?

---

### Post by foolsh on 2006-08-13
try 
sudo apt-get install menu
it will make a debian entry in your menu with alot of programs that i found do not show up automatically  
im not sure if you need to enable backport repositories for this though
other than that you can manually edit the menu and add entries for the games

---

### Post by Steve S. on 2006-08-14
> **foolsh said:**
> try 
sudo apt-get install menu
it will make a debian entry in your menu with alot of programs that i found do not show up automatically  
im not sure if you need to enable backport repositories for this though
other than that you can manually edit the menu and add entries for the games

I'll check on the Debian thing, foolsh, but how do you manually edit the menu?

---

### Post by foolsh on 2006-08-14
right click the applications menu and choose edit menu
in the window that opens select which entry you want to add the games in i.e. games. then click file > new entry then you can browse to where the games are installed. you can give it a name add comments choose an icon
very tedious 

good luck

---

### Post by Steve S. on 2006-08-14
> **foolsh said:**
> right click the applications menu and choose edit menu
in the window that opens select which entry you want to add the games in i.e. games. then click file > new entry then you can browse to where the games are installed. you can give it a name add comments choose an icon
very tedious 

good luck

Sure enough.  I had discovered the menu edit thing on my own a while back, but it would allow me to add some games, but not many of the ones I had added.

I ran the menu install, and EVERYTHING is in that menu; I mean, Ruby programming stuff that I had forgot about, OpenOffice stuff, not to mention the games were even categorized.

Why is that?  Why don't they show up on the menu right away?  Anyone know?

Either way, you rock, foolsh.

---

### Post by eqisow on 2006-08-14
You can use the Menu Editor in the Accessories menu to add menu entries manually. I'm not sure if that's the exact name, since I haven't used Gnome in a bit, but it's something like that.

Edit: Meh, looks like I was too slow.

---

