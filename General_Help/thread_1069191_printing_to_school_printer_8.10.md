---
title: "printing to school printer 8.10"
date: 2009-02-13
forum: General Help
---

### Post by evrkusd on 2009-02-13
hey

i've been trying to print to my school's campus-wide printing queue using cups but i can't seem to make it work. my school has instructions for both mac and windows which i've included below. I tried setting up a user/ password account in ubuntu to see if that would make it authenticate automatically (like in the mac instructions) but it didn't seem to help. usually cups finds the printer but i can't print to it or see anything in the queue (which should have everyone's print jobs). Is there a way to add authentication in cups that could help/ has anyone had a similar problem?
thanks.

MacOSX
    * You must create an administrator-equivalent account using your Brown username and log into that account to configure IP printing.

   1. From the Finder, open Printer Setup Utility (Go..Utilities, double-click Printer Setup Utilities).
   2. Click the Add icon to add a printer.
   3. From the first drop-down menu, select IP Printing.
   4. Next to Printer Type, select LPD/LPR.
   5. For Printer Address, enter uniprint.ad.brown.edu.
   6. For Queue Name, enter PAWPrints.
   7. From the Printer Model list, select HP.
   8. From the HP Printer list, select HP Laserjet 9000 Series. Note: If HP Laserjet 9000 does not appear in the printer list, follow the steps above to obtain the HP Laserjet 9000 printer drivers.
   9. Click the Add button.

To configure the PAWPrints queue on your Windows computer:

   1. Select Run from the Start menu.
   2. Enter \\uniprint.ad.brown.edu\PAWPrints in the Open field.
   3. You will be requested to authenticate. Enter ad\username in the name field, then your password.
   4. The Connect to Printer dialog box will appear. Click Yes.

---

### Post by jman6495 on 2009-02-13
hi
it might just be the network.
ask your i.t staff if the network allows printing from a linux box.
can you use your pc to connect  to the net by the same network?
hope this helps

   jman6495

---

### Post by dcstar on 2009-02-13
> **evrkusd said:**
> hey

i've been trying to print to my school's campus-wide printing queue using cups but i can't seem to make it work. my school has instructions for both mac and windows which i've included below. I tried setting up a user/ password account in ubuntu to see if that would make it authenticate automatically (like in the mac instructions) but it didn't seem to help. usually cups finds the printer but i can't print to it or see anything in the queue (which should have everyone's print jobs). Is there a way to add authentication in cups that could help/ has anyone had a similar problem?
thanks.
........

You should try finding the printer via Places-Network and then connecting to it via that path - that may set up the authentication stuff.

---

### Post by evrkusd on 2009-02-14
I can connect to their network with my computer. I'm currently not on their network but connected to them via vpn which if I was on a windows or mac would allow me to print to their queue pretty easily (following the instructions i posted)

i checked in places-network and I don't see anything listed. 

not sure what else to try besides asking people at my school. any other ideas?>

---

