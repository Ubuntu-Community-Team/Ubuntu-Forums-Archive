---
title: "I can't print white text on a black bakcground."
date: 2005-05-27
forum: Desktop Environments
---

### Post by valadil on 2005-05-27
Hi there.  I've got a cranky HP OfficeJet v40 that doesn't seem to want to print white text on a black background.  I was trying to print up a pdf (that had been printing correctly in previous installations) and the white text in the pdf was getting blacked out by the black background.

At first I thought it was since I was printing with lp, so I tried printing from evince and gpdf, but that made no difference.  I was gonna try acroread, but I couldn't find an amd64 version and I'm too lazy to set up a chroot tonight.

Eventually I tried printing a test page.  If you've ever printed a test page in ubuntu, you know it gives you a page of scaled color.  The color scales from black or white to the full color in 10% increments.  The percentage of color is printed in each filed of color.  For whatever reason, each block that is 100% black (or 0% color) gets no label.  90% black (or 10% color) has a white label that looks just fine.  

Any ideas?  I realize this is a very specific problem and I'd be surprised if any of you have dealt with it before.

---

### Post by camp on 2005-05-27
Hi valadil,

I'm not sure I'm following you... but... I've never heard of a plain and simple printer that can print white color!
If you look at the cartdriges installed in your printer, you probably got one black and one with yellow, red and blue. No white... White is one of the basic colors, you can't combine other colors to get white.

Well... hope this help, and if you have a printer with a white cartdrige, then I better shut up!   :-#   ;-) 
/JC

---

### Post by valadil on 2005-05-27
Sorry, when I said print white, I mean leave a blank white spot.  I have a pdf with several black boxes in it.  In those boxes is white text.  My printer fails to print around the text, and just prints all black in the boxes.

Behold:  [http://people.brandeis.edu/~sagotsky/out.jpeg](http://people.brandeis.edu/~sagotsky/out.jpeg)

I circled the areas that are all black and are missing the white text that should be there.  Note that the white boxes with a black forground (in cyan, magenta, yellow, and black) all have their black text.

---

### Post by camp on 2005-05-27
Hi again,

Okay!... Now I undertand.   ;-) 
But I'm sorry, I'm using CUPS for printing, so I get a different test-page. I have my printer attached to my server, not my desktop. Try printing via CUPS.

Have a nice weekend!
/JC

---

### Post by valadil on 2005-05-28
I am using cups.  That test page in the link comes from gnome-cups-manager.  localhost:631 gives me a different one, that appears normal.

---

### Post by trash on 2005-05-28
I could be wrong but i think in the printing world that is a bleed issue, the more intense the color the more the bleed shows hence covering the white text... I don't think there is anything you can do about it either... as I say I could be wrong:)

---

### Post by valadil on 2005-05-28
Except that the printer works fine in windows.  

Considering how infrequently I have to print white on black, I don't mind a boot to windows to do so.  But it would be nice to get my printer working 100%.

---

### Post by trash on 2005-05-28
it would be cool to see how that page printed in windows then, could be the quality of the drivers itself?

---

