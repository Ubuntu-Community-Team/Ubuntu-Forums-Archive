---
title: "Launching multiple applications from a script?"
date: 2009-04-25
forum: General Help
---

### Post by antieuclid on 2009-04-25
With all of the problems with Jaunty and multiple desktops, I find myself having to write launching scripts for all my applications. Some of them I always launch at the same time, and I was hoping to launch them all with one script while I was at it. But it waits until I quit the first app before it launches the second. How do I tell it to just keep going after launching the first program?

---

### Post by lisati on 2009-04-25
Put an "&" at the end of the line where you start up an application.

---

### Post by antieuclid on 2009-04-25
Thanks! I've been trying to figure that out all day.

---

### Post by Dr_Willis on 2009-04-25
if launching things to the background from a terminal. such as  the following


$ spiffycommand &
$ otherSpiffyCommand &

  
do NOT NOT NOT just 'hit the close button' to close the terminal. 

use the 'exit' command. Otherwise all the commands you launched to the background might be forced to close. I see this asked in the irc channel about once a week. So i figured it would be worth  mentioning.

$ command1 &
$ command2 &
$ exit

Also a read of a few tutorials on 'Job control in bash' is some time well spent. :) [http://www.faqs.org/docs/bashman/bashref_77.html](http://www.faqs.org/docs/bashman/bashref_77.html)



also another way to put things in the background (in case you forget the &)

$**spiffycommandthattakesaLONGtim**e
^z  (control z)
[1]+ Stopped spiffycommandthattakesaLONGtime
$ **bg**
[1] spiffycommandthattakesaLONGtime &


This is handy when you dont want to open a new terminal.

Good luck.

---

