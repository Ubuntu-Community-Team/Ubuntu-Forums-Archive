---
title: "Boot conky on startup only if internet connected"
date: 2009-01-08
forum: General Help
---

### Post by Gizmo688 on 2009-01-08
What kind of for/if loop could i add to my conky script to make it to where it would only run the conky files if there was a valid interent connection? i know how to write loops, im just not sure of the variable names and arguments to use.

if(eth1 is connected){
   boot...
}
else
   wait 20 seconds and try again



would something like this even work?

---

### Post by easybake on 2009-01-08
Your best bet would be to just put an if statement at the beginning of the conky and put the endif at the end of the conkyrc. That way conky would always be running it just wouldn't be displaying anything until you were connected.

---

### Post by Gizmo688 on 2009-01-16
but what are the variables i use?

im pretty sure its not "if(eth1==TRUE)" or anything like that

---

