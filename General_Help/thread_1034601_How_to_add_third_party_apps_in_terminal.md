---
title: "How to add third party apps in terminal"
date: 2009-01-08
forum: General Help
---

### Post by vwbeamer on 2009-01-08
This is more of a Mint question. 

I have Mint 6.0 and I want to add boxee ( went public today)

Their instructions-

   1. Go to System > Administration > Software Sources.
   2. In Sources Software dialogue, select Third-Party Software tab, click Add, and enter:
          * for Hardy: deb [http://apt.boxee.tv](http://apt.boxee.tv) hardy main
          * for Intrepid: deb [http://apt.boxee.tv](http://apt.boxee.tv) intrepid main
   3. After closing this dialogue you can either use Synaptics and select Boxee for download, or use a terminal window, and enter sudo apt-get install boxee.

To run Boxee, Applications > Sound & Video > Boxee

My problem is Mint doesn't have Software Sources ( why? seems crazy to take needed stuff out of Ubuntu?)

How can i add Boxee in the terminal???

---

### Post by MighMoS on 2009-01-08
```
sudo su -
echo "deb http://apt.boxee.tv intrepid main" > /etc/apt/sources.list.d/boxee.list
apt-get update
apt-get install boxee
exit

```

---

### Post by vwbeamer on 2009-01-08
Thanks for the fast reply.:D

I copy and pasted that in the terminal and at the end it asks?

"After this operation, 30.2MB of additional disk space will be used.
Do you want to continue [Y/n]?** Y**
Abort.

I typed 'Y" and it still aborts.

---

### Post by vwbeamer on 2009-01-08
Left the "exit " off and now it works, Thanks!

---

