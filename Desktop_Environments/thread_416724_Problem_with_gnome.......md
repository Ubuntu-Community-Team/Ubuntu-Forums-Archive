---
title: "Problem with gnome......"
date: 2007-04-21
forum: Desktop Environments
---

### Post by Immolatus on 2007-04-21
All the other questions here seem so much more serious but anyhow.
I've got an odd question about gnome: When ever I switch to a really dark theme, some of the text for certain sites in firefox  become grayed out and unreadable mainly though it only occurs with Gmail. Thats my business mail otherwise I would just not use it.

Any thoughts??

---

### Post by Theimon on 2007-04-21
There are a few dark themes out there that supply a custom .css file so all text is readable again. It has to do with the dark theme using light coloured text. It forces Firefox to use the light coloured text as well, hence you get the unreadable lines (light text on light background). 
For example Elegance supplies such a .css file. In your ~/.mozilla folder there should be an example file which you could edit to get the same result.

---

### Post by Immolatus on 2007-04-21
> **Theimon said:**
> There are a few dark themes out there that supply a custom .css file so all text is readable again. It has to do with the dark theme using light coloured text. It forces Firefox to use the light coloured text as well, hence you get the unreadable lines (light text on light background). 
For example Elegance supplies such a .css file. In your ~/.mozilla folder there should be an example file which you could edit to get the same result.

I see, is there a way to set firfox to not accept system themes instead?

---

### Post by Theimon on 2007-04-21
> **Immolatus said:**
> I see, is there a way to set firfox to not accept system themes instead?

Not that I'm aware of....

---

### Post by ComplexNumber on 2007-04-21
> **Immolatus said:**
> All the other questions here seem so much more serious but anyhow.
I've got an odd question about gnome: When ever I switch to a really dark theme, some of the text for certain sites in firefox  become grayed out and unreadable mainly though it only occurs with Gmail. Thats my business mail otherwise I would just not use it.

Any thoughts??
download [this]("http://gnome-look.org/content/show.php/Kore-GTK?content=55744") dark theme to overcome the unreadable text problem in firefox. after you've downlaoded it, exract the file, and in it, you will find a css file and instructions (instructions below) it worked for me.

i've attached a screnshot of YouTube to show you. before i made the change, the background of where i've typed "testing testing" was completely black". now its white.


EDIT: seems like i've merely said the same thing as what Theimon has said.

> Firefox:
--------
If web forms and controls appear dark and unreadable you need to edit the css files that Firefox uses. The file location may vary on different linux distributions. Do the following in a terminal:

1. Backup the original file:
sudo mv /usr/lib/firefox/res/forms.css /usr/lib/firefox/res/forms_backup.css

2. Replace it with the provided forms.css
sudo mv "downloaded location"/GTK2/forms.css /usr/lib/firefox/res/forms.css

3. Then you need to edit html.css:
sudo gedit /usr/lib/firefox/res/html.css

Around line 60, change:

body {
  display: block;
  margin: 8px;
}

To:

body {
  background-color: white;
  color: black;
  display: block;
  margin: 8px;
}

Save the file, then restart Firefox, and you should have standard colours.

---

### Post by Immolatus on 2007-04-21
> **ComplexNumber said:**
> download [this]("http://gnome-look.org/content/show.php/Kore-GTK?content=55744") dark theme to overcome the unreadable text problem in firefox. after you've downlaoded it, exract the file, and in it, you will find a css file and instructions (instructions below) it worked for me.

i've attached a screnshot of YouTube to show you. before i made the change, the background of where i've typed "testing testing" was completely black". now its white.


EDIT: seems like i've merely said the same thing as what Theimon has said.

:guitar: THANK YOU!! That worked great, the only question I have is if I have to edit html.css and move things around like that if I change themes? Or is it permanent?

---

### Post by Theimon on 2007-04-21
> **Immolatus said:**
> :guitar: THANK YOU!! That worked great, the only question I have is if I have to edit html.css and move things around like that if I change themes? Or is it permanent?

It should be permanent, so that even if you change themes, the settings would remain the same. But to be sure, keep a backup of edited file just in case and you'd be home-free :)

Edit: ComplexNumber; you did say the same thing but you supplied a tad more info so credits to you ;)

---

### Post by Immolatus on 2007-04-22
Hey, thanks guy's. I did make a backup, fallowing the instructions in the Kore-gkt theme package.
And the changes are permanent.
Thanks again, that was really making me crazy.:)

---

