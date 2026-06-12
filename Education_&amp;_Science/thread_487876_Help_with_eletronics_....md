---
title: "Help with eletronics ..."
date: 2007-06-29
forum: Education &amp; Science
---

### Post by hockey97 on 2007-06-29
Hi I just got my first bread board and It's a wish baard, I have experiane with bread boards but never had this type I never owned one before, It has 4 holes where I can put 4  special screws and they have a nut for the otther side of the board.

the bread board is ontop of a sheet of steel and I never used such a board, I got this one ebay by the way,

the seller said that it has a power supply with it, but I don't see it, The name of the board is WISH Board.

to me it look's like I need to buy a power supply for the board and hook it up with the screws but never used this before I used a small bread board and used a special power supplyer gave one Voltage one positive and one neg terminal I would but the positive on the positive bus strip, and the neg on a neg bus strip.

and Does anyone know of a good eletronics supplier?? 

and What Eprom chip programmer should I get, I don't knwo what I am going to use, maybe a dip chip,

but what's today's top flash chip for today's eletronics?? like EEprom or something.

I got eagle cad I don't know if it's  any good, I got the free version.

---

### Post by boz on 2007-06-30
> 
Hi I just got my first bread board and It's a wish baard, I have experiane with bread boards but never had this type I never owned one before, It has 4 holes where I can put 4 special screws and they have a nut for the otther side of the board.

the bread board is ontop of a sheet of steel and I never used such a board, I got this one ebay by the way,

the seller said that it has a power supply with it, but I don't see it, The name of the board is WISH Board.

to me it look's like I need to buy a power supply for the board and hook it up with the screws but never used this before I used a small bread board and used a special power supplyer gave one Voltage one positive and one neg terminal I would but the positive on the positive bus strip, and the neg on a neg bus strip.


I've never used such a board before.  The good news is that you can apply power to your breadboard any way you want to (as long as you don't short power and ground together).  You don't necessarily have to use the screws that came with the board.  I usually just connect a jumper to an alligator clip and sick the other end of the jumper in one of the power buses.


> 
and Does anyone know of a good eletronics supplier?? 


I usually go through DigiKey or Mouser.

> 
and What Eprom chip programmer should I get, I don't knwo what I am going to use, maybe a dip chip,

but what's today's top flash chip for today's eletronics?? like EEprom or something.


I honestly don't know.

> 
I got eagle cad I don't know if it's any good, I got the free version.


Eagle CAD is one of the best out there.  I also like PCB from the gEDA suite ([http://www.geda.seul.org/](http://www.geda.seul.org/)).  If you anticipate that you will be doing SPICE simulations often, I recommend that you install the entire gEDA suite and familiarize yourself with it.  It will make you a better EE in the end.  Although PSPICE is okay and it's a fully integrated IDE, I think it tends to make you a bit more dull and clueless in the end.

---

### Post by hockey97 on 2007-07-02
Well I used at school a regular sized bread board, and i used 1 voltage and ground we took wires wrapped one end to the powersupply for positive and one neg or gound, and the other side to the poistive bus strip.

I bought this board that's huge size board and has 4 holes where I can put 4 screws/nuts that 3 are voltage and 1 is ground,  they said that it supports buses, I don't know what that mean's.

I don't know how should I hook up  a power supply to it?? they said it already has a power supply but don't see one.

I am thinking to use an old computer power supply, I guess, do you think that's safe??

---

### Post by twidget on 2007-07-10
first off get yourself good book on electronics and read it. my recommendation is "Art of Electronics" by horowitz and hill. is the best one i've found. 
in order to tell you what kind of eeprom chip you should get i need to know what you're using it for. 
EAGLE is an excelent program but I've never gotten the one from the repos to work right. my recomendation ,if you run into trouble, is to download the .tgz package from the cadsoft website, unzip it somewhere in your home folder where you want it installed. then go into the unziped folder find the bin folder find the EAGLE executable inside it and put link to it on your desktop. then just click on the link whenever you want to start it up. 
there are plenty of links on google on how to make a benchtop powersupply out of an old PC PSU. i think it boils down to jumpering the green wire on the main ATX connector to ground. if you blow yourself up i'm not responsible :). now you have +5, +12 and i think a few negative voltages. if you need any other voltage (3.3 comes to mind) you are going to have to get yourself a voltage regulator to put between the PSU and your circuit. Digi-key has thousands of them.read the datasheets and pick one that works.
finally this isnt really an electronics board you can better responses to your electronics questions in electronics forums.

---

