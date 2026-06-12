---
title: "opening .mdb files with mdb viewer in juanty"
date: 2009-04-29
forum: General Help
---

### Post by DrSB on 2009-04-29
Hi all,

New to linux so need some urgent help if possible. I am trying to open an .mdb (Ms access file) file for my GF (she tells me its a collection of past exam questions). 

I only run os x and ubuntu (jaunty) so dont have acess to windows. I have tried opening the file using mdb viewer but every time i try to open it within the programme it just quits it self. I was wondering if anyone has had any similar problems or knows of any solutions/alternatives. I have already tried to open it in open office, while it does open i get about 2,500 pages with all kinds of strange characters on the screen and no real readable text! 

Please please bear in mind im new to linux and also not a computer programer etc :( so please keep it as user friendly as possible :) 

Thanks guys and hope to hear from you soon

DrB

---

### Post by Bindsa on 2009-04-29
Try to open the file with a plain-text editor, if that only shows up weird symbols try a Hex-editor. However, it will be hard to read the contents because Microsoft doesn't uses an easy save technique. 

Hope this helped you.

--
B!ndsa

---

### Post by DrSB on 2009-04-29
> **Bindsa said:**
> Try to open the file with a plain-text editor, if that only shows up weird symbols try a Hex-editor. However, it will be hard to read the contents because Microsoft doesn't uses an easy save technique. 

Hope this helped you.

--
B!ndsa


Hi Bindsa

Thanks for your help, have tried all that you suggested above but alas to no avail :) but thanks anyway. Back to work, but will check back later to see if anyone else has any ideas.

Thanks again

DrB

---

### Post by MatMan on 2009-05-25
Hi DrB
I have the same problem and no solution. Did you find one?

---

### Post by Akhnatoun on 2010-05-21
Which mdb viweer you are using?

I am using Ubuntu Lucid and I had the same problem with an .mdb file which was created by Motorolla.

I have solved this problem by running this command in terminal:

sudo apt-get install mdbtools-gmdb

and then I found the program in the Applications>Office>Mdb Viewer

I opened my file and it worked correctly.

I hope this is helpful

---

