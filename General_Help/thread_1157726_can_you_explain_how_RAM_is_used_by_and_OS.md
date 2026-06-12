---
title: "can you explain how RAM is used by and OS?"
date: 2009-05-13
forum: General Help
---

### Post by mahela007 on 2009-05-13
I read the howstuffworks.com article on ram and it said that most applications are purged from RAM after they are closed. However it seems that applications start up much faster once they have been opened previously. If the applications has been deleted from RAM how does it load faster the second time it is opened?

---

### Post by Locutus_of_Borg on 2009-05-13
an OS will cache and keep data within RAM until the computer is rebooted or something else takes its space

---

### Post by geraldvillorente on 2009-05-13
RAM is used to store volatile task(s)(all open program(s)/application(s) and OS) when system is running...if you are familiar with cache...thats exactly the answer to your question

---

### Post by Yellow Pasque on 2009-05-13
The application data doesn't actually get swapped out until you start running out of physical memory. On modern hardware (>= 2GB RAM), it's becoming increasingly difficult for a lot of users to reach the physical RAM limit, unless they're doing RAM-intensive tasks like virtualization or loading huge images in GIMP.

For a better understanding of how virtual memory works, see: [http://andrew-gray.com/unixfaq/explain_vm.shtml](http://andrew-gray.com/unixfaq/explain_vm.shtml)

---

### Post by CatKiller on 2009-05-13
Linux handles RAM differently from Windows. Windows will aggressively empty the RAM, whereas Linux keeps a file cache in memory in case you need to use those files again. Those files are only removed from the RAM when that RAM actually needs to be used for something else, using the principal that empty memory is wasted memory. It takes the same amount of time to write something to memory whether the space that's being written to had something in or not, so there is no cost associated with this approach, and it improves performance if you did need those files again because you then don't have to load them from the hard drive again which is comparatively really slow.

---

### Post by mahela007 on 2009-05-13
So basically if I open say, Open office then the whole app will be loaded into RAM. If I close it then it will still be stored in RAM untill another application needs that space? If I use it in windows then the application will be deleted from RAM as soon as I close it?

---

### Post by CatKiller on 2009-05-13
> **mahela007 said:**
> So basically if is open say. Open office then the whole app will be loaded into RAM. If I close it then it will still be stored in RAM untill another application needs that space? If I use it in windows then the application will be deleted from RAM as soon as I close it?

Pretty much, as I understand it. Except when memory is in high demand.

---

### Post by Chris Musampa on 2009-05-13
> **mahela007 said:**
> So basically if is open say. Open office then the whole app will be loaded into RAM. If I close it then it will still be stored in RAM untill another application needs that space? _If I use it in windows then the application will be deleted from RAM as soon as I close it?_

Not so.  I don't know if windows caches the same way as linux but it (i use XP at work) definitely does not immediately wipe apps from RAM as soon as you close them.

---

### Post by Legace on 2009-05-13
> **Chris Musampa said:**
> Not so.  I don't know if windows caches the same way as linux but it (i use XP at work) definitely does not immediately wipe apps from RAM as soon as you close them.

Yeah, Windows keeps the DLL's in RAM for some time..

---

### Post by Tipped OuT on 2009-05-13
> **Legace said:**
> Yeah, Windows keeps the DLL's in RAM for some time..

Yes, Windows keeps them in the RAM for some time, it supposedly helps with performance, even though Vista is slow as a dog with no legs. :lolflag:

---

### Post by Legace on 2009-05-13
> **Tipped OuT said:**
> Yes, Windows keeps them in the RAM for some time, it supposedly helps with performance, even though Vista is slow as a dog with no legs. :lolflag:

Yup. The OS itself takes up all the RAM so that your own apps don't have enough memory..

You should try Windows 7. It's much faster :)
And I am not saying that you should dump Linux, but just test it. It's pretty good.. (I'm staying with Ubuntu and my >16 sec boot time)

---

### Post by mahela007 on 2009-05-14
What's DLL?

---

### Post by pbpersson on 2009-05-14
> **mahela007 said:**
> What's DLL?
[URL="http://www.easydesksoftware.com/dll.htm"]
http://www.easydesksoftware.com/dll.htm[/URL]

---

