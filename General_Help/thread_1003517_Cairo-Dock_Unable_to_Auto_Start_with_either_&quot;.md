---
title: "Cairo-Dock: Unable to Auto Start with either &quot;Sessions&quot; or Startup Script"
date: 2008-12-06
forum: General Help
---

### Post by theo.potgieter75 on 2008-12-06
Hi

I have searched all the forums and can not find a similar issue. I loaded Cairo-dock, and added a script in the init.d folder to start it up where the command line is Cairo-dock. when i click on the script, it initiates Cairo-dock, but for some reason it does not start it up when i log in. I have also added this in sessions under system preferences.

One thing that i have noticed however, is that when i open up a terminal window, and i initialize Cairo-dock through there, it runs perfectly, but when i close the terminal, cairo-dock shuts down and disappears.

I'm running intrepid on VMware Fusion.

Thank you

---

### Post by Idefix82 on 2008-12-06
> **theo.potgieter75 said:**
> 
One thing that i have noticed however, is that when i open up a terminal window, and i initialize Cairo-dock through there, it runs perfectly, but when i close the terminal, cairo-dock shuts down and disappears.


That's normal and is the same for any program you start through the terminal. If you want the program to persist after you close the terminal, append an ampersand to the end of the line, e.g.
```
cairo-dock &
```

Why it doesn't start when you add to your session, I don't know. But the init.d is definitely the wrong place to start it. You only want it to start when you log in, not when Ubuntu is booting. Besides, I hope that you are aware that just adding the script into the init.d folder won't make it start. Have a read here: [http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/]("http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/")
But as I said, don't add cairo-dock to the init.d start up scripts.

---

### Post by eternalnewbee on 2008-12-06
This helped me:

---

### Post by eternalnewbee on 2008-12-06
When you enter cairo-dock, don't use capital letters.

---

### Post by theo.potgieter75 on 2008-12-06
Thanks. the non capitals seemed to have done the trick. The reason i added in init.d was because of some ubuntu formum posts i have read advising other users to do so.

Apending the ampersand at the end of "cairo-dock &" still did not keep cairo-dock running when i closed the terminal window.

Thanks for the help.

Nice Neural network background :)

---

### Post by eternalnewbee on 2008-12-06
So you're good to go now?
If so, I'm glad I could help.
If your problem is solved, don't forget to mark it so, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.
PS: Welcome to the Ubuntu Community:D
> Nice Neural network background
You can find it here:
[http://images.google.co.uk/images?hl=en&q=dual%20neuron&um=1&ie=UTF-8&sa=N&tab=wi](http://images.google.co.uk/images?hl=en&q=dual%20neuron&um=1&ie=UTF-8&sa=N&tab=wi)

---

