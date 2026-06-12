---
title: "How to install Limewire"
date: 2005-12-10
forum: Desktop Environments
---

### Post by jørgen on 2005-12-10
How can i install Limewire on Ubuntu?

---

### Post by DJ_Max on 2005-12-10
Have you read the manual?
[http://help.ubuntu.com/starterguide/C/ch03s06.html#id2529193](http://help.ubuntu.com/starterguide/C/ch03s06.html#id2529193)

---

### Post by Rackerz on 2005-12-10
Here is my post on how to install LimeWire. You should find all the information needed there. [http://ubuntuforums.org/showthread.php?t=91222](http://ubuntuforums.org/showthread.php?t=91222)

---

### Post by jørgen on 2005-12-10
I have tried. But i cant make it work. After i have installed Limewire nothing happens when i click on the icon in the menu.

---

### Post by jørgen on 2005-12-10
Is there nobody here who knows what i can have done wrong?

---

### Post by taurus on 2005-12-10
I installed limewire the old fashion way.  I downloaded it from its website and unpacking it in my $HOME/bin, I created a link to it and it is working just fine...  ;)

---

### Post by jørgen on 2005-12-10
Well the problem is that i dont know how to do that :)

---

### Post by taurus on 2005-12-10
> **j&#248 said:**
> Well the problem is that i dont know how to do that :)
And I assume you want me to show you how to!!!  ;) 
Make sure you have installed java, j2re or j2sdk, using synaptic first since limewire will look for it...
Then, head over to [http://www.limewire.com/english/content/home.shtml](http://www.limewire.com/english/content/home.shtml) and click on "Download" on the upper left corner.  Click "Get Basic" and pick "I will not use LimeWire BASIC for copyright infringement."  then "Continue>".  Now, scroll down and click "? Other" (the last option).  Wait for the download to finish and open up a terminal and type

mkdir bin
mv LimeWireOther.zip bin 
(assuming that you have firefox save all the downloads to your home's directory...)
cd bin
unzip -x LimeWireOther.zip
cd LimeWire
./runLime.sh &

Now, configure it to whatever you'd like.  PM me whether it works or not...

---

