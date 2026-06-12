---
title: "Changing menu font color in Firefox for those dark themes."
date: 2007-07-18
forum: Desktop Environments
---

### Post by xl_cheese on 2007-07-18
I created a dark theme where all the os menus are black with white text.

Well firefox didn't like that much.  I found a couple firefox themes that would correct the problem, but I didn't really care for them.

I finally figured out the correct way to force firefox to use a specific color.

Create this file:

```
/home/*/.mozilla/firefox/*.default/chrome

userChrome.css
```

Stick this in there:

```
menubar, menubutton, menulist, menu, menuitem {
  font-family: helvetica !important;
  font-size: 4mm !important;
  color: black ! important; 
}
```

restart firefox.

In my case I needed black font for firefox as it was trying to use my theme's white font.

Other options you can add are:

 font-style: italic !important;
 font-weight: bold !important;

---

### Post by format_c on 2007-11-21
Hi great work.
But based on your work I made some advantages that fixed some more problems with firefox and thunderbird for me.

Hi I combined The "Orange-LiNstaBlackPlastic" Theme as window content and "Elegance" theme as window borders.

But in firefox and thunderbird some popupmenus (e.g. autocomletion) are shown with black color.
In thunderbird. The font color of the select menu to choose the sending account was white where black would be much better.

So I modified your file and copied it into the firefox profile and the thunderbird profile.
The both mentioned files look like this:
```

**format_c@boston ~ $** cat .thunderbird/*.default/chrome/userChrome.css
menubar, menubutton, menu, menuitem, menupopup, popup > * {
  font-family: sans !important;
  font-size: 10pt !important;
  color: white !important; 
}

**format_c@boston ~ $** cat .mozilla/firefox/*.default/chrome/userChrome.css
menubar, menubutton, menu, menuitem, menupopup, popup > * {
  font-family: sans !important;
  font-size: 10pt !important;
  color: white !important; 
}
[B]
format_c@boston ~ $ [/B]

```

So now the affected elements look as pretty as the rest. refer the screenshots

**Thunderbird**
[IMG]http://www.alexanderkoeppe.name/pub/thunderbird.png[/IMG]

**Firefox**
[IMG]http://www.alexanderkoeppe.name/pub/firefox.png[/IMG]

---

### Post by bford16 on 2007-11-24
This works great, but only if I don't use a light theme like Clearlooks.  As soon as I change themes, I have to change the userChrome files.  Any idea how to work around this?

---

### Post by gooner11 on 2007-12-01
Where do you put that code? In the terminal or where you put the url in firefox? I tried both and they dont work. Forgive my ignorance as I'm new to linux and its themes.

---

### Post by Newcomer Johannes on 2008-01-27
It's a wonderful Theme:)
Now the Firefox looks great, too. thank you very much.
@gooner11
You have to write in the Terminal:
```
gedit ~/.mozilla/firefox/mic4y1e.default/chrome/userChrome.css
```
then you paste this into it
[I]menubar, menubutton, menu, menuitem, menupopup, popup > * {
  font-family: sans !important;
  font-size: 10pt !important;
  color: white !important; [/I]
save and restart firefox

> Forgive my ignorance as I'm new to linux and its themes.
There is no problem to ask something, lots of people help willingly you.

---

### Post by kaufmannn on 2008-02-03
Thanks for the help, I had this problem too with the same theme as format_c, however, I realized that you only need to tell it to override the colour... I really don't know why you people are telling everyone to override the font family and size - it's not needed. It's not going to hurt, but that doesn't make it right.

I'm no expert in coding (of any language) so I have two questions for those out there with more knowledge... in the address bar drop down the url's are now white, yet the descriptions beside them are in a medium grey. Is it possible to change that through the chrome.css also? What would that value be called though?

Also, unrelated to menu font colour I have the following problem (look at the image: top is swiftweasel and bottom is nautilus). In Swiftweasel when a menu is chosen the menubar button looks all wonky (it's the image used when you hover over a panel button), I don't know how to change it to the regular menubar button image. If someone knows where this value is, I'll know how to change it.

---

### Post by univtex34 on 2008-03-27
Ok I have tried eveything I possibly can to get this to work, but it wont... would someone who has this working post a screenshot of their userChrome.css file so I can make sure I'm not an idiot...

TIA

---

### Post by agibby5 on 2008-05-08
> **format_c said:**
> Hi great work.
But based on your work I made some advantages that fixed some more problems with firefox and thunderbird for me.

Hi I combined The "Orange-LiNstaBlackPlastic" Theme as window content and "Elegance" theme as window borders.

But in firefox and thunderbird some popupmenus (e.g. autocomletion) are shown with black color.
In thunderbird. The font color of the select menu to choose the sending account was white where black would be much better.

So I modified your file and copied it into the firefox profile and the thunderbird profile.
The both mentioned files look like this:
```

**format_c@boston ~ $** cat .thunderbird/*.default/chrome/userChrome.css
menubar, menubutton, menu, menuitem, menupopup, popup > * {
  font-family: sans !important;
  font-size: 10pt !important;
  color: white !important; 
}

**format_c@boston ~ $** cat .mozilla/firefox/*.default/chrome/userChrome.css
menubar, menubutton, menu, menuitem, menupopup, popup > * {
  font-family: sans !important;
  font-size: 10pt !important;
  color: white !important; 
}
[B]
format_c@boston ~ $ [/B]

```

So now the affected elements look as pretty as the rest. refer the screenshots

**Thunderbird**
[IMG]http://www.alexanderkoeppe.name/pub/thunderbird.png[/IMG]

**Firefox**
[IMG]http://www.alexanderkoeppe.name/pub/firefox.png[/IMG]

For me there's no /home/xxxx/.mozilla/thunderbird folder... Can I just create the structure?  How do I know what to name * in *.default?

---

### Post by HybridZero on 2008-06-07
Very sorry to bump this, but I have a related question.

I'm using MurrinaDBO as my theme, and Firefox's menu was displaying white text on a white background for the menubar (Screenshot 1). I modified the menubar text to be black using:

menubar, menubutton, menulist, menu {
  font-family: sans !important;
  font-size: 9pt !important;
  color: black ! important; 
}

which worked for the menubar, but now all of my submenus are also displayed as black on a black background (both bookmarks folders and submenus in other menus - Screenshot 2). How can I get the submenus back to being displayed with white text while keeping the main menu bar text as black?

**UPDATE:** I was able to solve the problem by relying on the menu ids in order to theme the menubar items only while leaving the submenu colors the way they were. Not the most elegant solution probably, but it's the only one I've found so far.

The userChrome.css looks like this:

menu#file-menu {color: black ! important;}
menu#edit-menu {color: black ! important;}
menu#view-menu {color: black ! important;}
menu#history-menu {color: black ! important;}
menu#bookmarksMenu {color: black ! important;}
menu#tools-menu {color: black ! important;}
menu#helpMenu {color: black ! important;}

---

### Post by jay019 on 2008-06-19
Try...

```

menubar, menu {
  color: black !important;
}

/* change font color of popup menus */
menupopup > menu,
menupopup > menuitem,
popup > menu,
popup > menuitem {
  color: white !important;
}

```

For something like this:

---

