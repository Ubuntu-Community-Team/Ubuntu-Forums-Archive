---
title: "Black Theme W/ OpenOffice &amp; Firefox"
date: 2009-05-02
forum: Desktop Environments
---

### Post by sandman3838 on 2009-05-02
Hello

I have to tell you that I really do like some of that black themes that I have picked up lately.  Wouldn't you know it just about everyone has an issue with the colors in Firefox and Openoffice 3.01.  Also, with OpenOffice there is also the issue with the icons are missing, it's all text.

Now Manually I went into OpenOffice and I changed the colors even though the Icons are missing.  

I have tried a few of some fixes that I found googling and in here but they haven't helped fix the Missing Icons In Openoffice or Firefox?  Perhaps it's because everything is a later update since the fix was posted?

Suggestions or Links for help on this would be great.

My system is about a week old with Ubuntu 904 and Firefox.

---

### Post by Happy_Man on 2009-05-02
Openoffice just has *terrible* theming support. So, it's not really a problem with Ubuntu, per se, just with Openoffice in general. Sorry. :(

---

### Post by sandman3838 on 2009-05-02
I found this:

*************** 
Some dark GTK themes are compatible well with the OpenOffice.Org, such as DigitalDark, if the OpenOffice.Org, especially Calc, messes up with the dark theme, you can remove packages openoffice.org-gtk and openoffice.org-gnome to use the default style of OpenOffice.Org.

$ sudo apt-get remove openoffice.org-gtk openoffice.org-gnome

One day if you find a dark theme available, basically, you need only to install openoffice.org-gtk to make OpenOffice.Org to apply the theme.

$ sudo apt-get install openoffice.org-gtk
*************** 

It worked for me now when I change to any dark theme it seems that Open Office is left alone!

The only other issue I have to find is a fix for the SEARCH field in Google.  It's black!  I read something about the userContent.css file in Firefox.  Unfortunatly I havn't found the file yet.

---

### Post by Happy_Man on 2009-05-02
That's in ~/.mozilla/<long string of randomness>.default/chrome/userContent-example.css . You have to change the name of userContent-example.css to userContent.css before it'll work, though. Best of luck!

---

### Post by sandman3838 on 2009-05-02
Thanks that was it!
Now fire fox is fixed.

Thank you

---

### Post by northport on 2009-05-08
can you expand on what you did here. I cannot get it to work. Firefox 3.0 under Ubuntu 9.04 on my machine is not reading my userContent.css file

Thanks

---

### Post by northport on 2009-05-08
can you expand on what you did here. I cannot get it to work. Firefox 3.0 on my machine is not reading my userContent.css file

Thanks

---

### Post by sandman3838 on 2009-05-08
Sorry!
For FIREFOX I thought I had it fixed but it would seen that when I changed themes it came back.  Nuts!

As Happy_Man suggested earlier its a matter of renaming the UserContent.css file.  I took it one step further and saved the original.  Severial GTK themes out there in [http://gnome-look.org/content/search.php](http://gnome-look.org/content/search.php) supply a replacment file.  Unfortunatly I can't remember which one.  The Slickness Theme has one I believe?

Now I do have my original userContent-example.css or userContent.css saved from my original installation of Firefox.  I saved it before adding any themes.  I'll have to get back with you to see is I replace it again if it will hold?

My USERCONTENT-EXAMPLE.CSS file is in a hidden folder!
CTRL+H  to reveal the hidden folders.
You will find it here:
/home/USERNAME/.mozilla/firefox/88l7i7y8.default/chrome

I hope this helps!

---

### Post by sandman3838 on 2009-05-08
Sorry but the file replacement for me didn't work!
However I did some playing around and took it another way.

Some FireFox themes do a fine job om there own fixing most of the issues.
Try these themes, some make use of the black some block it, your choice.
You can go to Firefox Web site for these themes.

I like:
Noia 2.0
Nautipolis
Natural Classic
Modern Modoki
Little Fox
Gnome Classic
Fixdie (blue)  - My favorite
Classic Compact

Now as for the main search line Google!  Oh, my Home Page is Google.
I was thinking why fight it!  Take advantage of it!  
The Blackness can be your friend.
Try these as a possible Google Search replacement.  
They are using the Google search engine and they read really well.

[http://www.jabago.com/](http://www.jabago.com/)
[http://www.blackle.com/](http://www.blackle.com/)
[http://gblack.org/](http://gblack.org/)
[http://black-google.blogspot.com/](http://black-google.blogspot.com/)

I hope this helps?

---

