---
title: "Can I remove files I didnt nead?"
date: 2009-02-17
forum: General Help
---

### Post by casmok on 2009-02-17
OK a couple of questions concerning Media Player.

I downloaded a bunch of add on files, mainly codecs for Media Player. But I downloaded stuff I dont need and would like to remove them. Essentially I'd like to start again fresh.

So.. are these stored within media player it self in which case I could delete MP and then start agin from scratch...or are they stored somewhere else? In which case is there a log of recently added files that I can use to find them and then delete.

Maybe  a silly question but please help

Thanks :)

---

### Post by InspiredIndividual on 2009-02-17
This thread might be what you're looking for:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

I wouldn't advise you to find and delete files manually, unless you know exactly what you're doing.

---

### Post by casmok on 2009-02-17
Thanks for that. Thats useful reading!

No I'm not planning on just deleting at random. But I just wondered if there was a way of "undoing" what I'd downloaded? rather like add/remove programs in Windows.

Mike

---

### Post by InspiredIndividual on 2009-02-18
> **casmok said:**
> 
But I just wondered if there was a way of "undoing" what I'd downloaded? rather like add/remove programs in Windows.


Actually, Synaptic is like add/remove programs in Windows. In Windows you'd have exactly the same problem. Say you install application A and it needs Java. The installer proceeds to install Java for you so you can use A. If you don't want to use A anymore, you can deinstall it in the add/remove programs window. However, Java won't be uninstalled, despite the fact you don't need it anymore. Just an example. In Ubuntu, you can use deborphan for example to cover such cases, as explained in the link I posted.

---

### Post by Slim Odds on 2009-02-18
> **InspiredIndividual said:**
> Actually, Synaptic is like add/remove programs in Windows. In Windows you'd have exactly the same problem. Say you install application A and it needs Java. The installer proceeds to install Java for you so you can use A. If you don't want to use A anymore, you can deinstall it in the add/remove programs window. However, Java won't be uninstalled, despite the fact you don't need it anymore. Just an example. In Ubuntu, you can use deborphan for example to cover such cases, as explained in the link I posted.

You don't really need deborphan, Synactic has filters to do stuff like that.

Take a look at the existing filters, or create one yourself.

---

### Post by casmok on 2009-02-18
> **InspiredIndividual said:**
> Actually, Synaptic is like add/remove programs in Windows. In Windows you'd have exactly the same problem. Say you install application A and it needs Java. The installer proceeds to install Java for you so you can use A. If you don't want to use A anymore, you can deinstall it in the add/remove programs window. However, Java won't be uninstalled, despite the fact you don't need it anymore. Just an example. In Ubuntu, you can use deborphan for example to cover such cases, as explained in the link I posted.

Thanks for all the comments. I used Deborphan to clean things up. Actually it turned out I didnt have much that needed cleaning!
Thanks

---

