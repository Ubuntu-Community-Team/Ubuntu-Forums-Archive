---
title: "ATI drivers help, Beginner guidance is needed !"
date: 2009-05-01
forum: General Help
---

### Post by bael on 2009-05-01
Hi !
I'm totally new in Ubuntu and would like to have a beginner guidance if possible.
I do know some easy parts in 'terminal' and minor stuff.
I'm having trouble on installing drivers for my graphic card and don't know how to do it.

 ATI radeon 9600 series is the one i use and would like to have total beginner guidance so i won't make any mistakes, and that means ex. go to administration/systemtest/whatever, click this and click that, type this and go to 'whatever'.

Please help me :(

-Bael

---

### Post by ranthal on 2009-05-01
This should help get you started:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Went through it with my hd 4850 and it was pretty straightforward.

---

### Post by pastalavista on 2009-05-01
If you're using Jaunty (9.04) the ATI drivers aren't compatible yet. You should try System > Administration > Hardware Drivers to see if there is anything available for your video card yet. I'm still waiting. You could try installing 'envyng' which is a graphics card installer. In terminal type ```
sudo apt-get install envyng-core
``` and when it is done type  ```
sudo envyng -t
```. It's a simple tooland works pretty well but if it shows nothing under the 'recommended' column, don't try any of the others. I learned that lesson the hard way.

---

### Post by bael on 2009-05-01
Yes i do use jaunty 9.04.

i will try now both ways and see if i can solve this problem.

thanks guys.

---

### Post by AdamShumpisxXx on 2009-05-01
You'll have to use the open source driver already installed with Jaunty. The only ATI driver supported thus far is 9.4 and you're graphics card is not covered.

Sorry. There is nothing you can do. That's the main reason I ditched Jaunty. Go back to Intrepid!

---

### Post by bael on 2009-05-01
> **pastalavista said:**
> If you're using Jaunty (9.04) the ATI drivers aren't compatible yet. You should try System > Administration > Hardware Drivers to see if there is anything available for your video card yet. I'm still waiting. You could try installing 'envyng' which is a graphics card installer. In terminal type ```
sudo apt-get install envyng-core
``` and when it is done type  ```
sudo envyng -t
```. It's a simple tooland works pretty well but if it shows nothing under the 'recommended' column, don't try any of the others. I learned that lesson the hard way.

Any information when the driver update will come?

---

