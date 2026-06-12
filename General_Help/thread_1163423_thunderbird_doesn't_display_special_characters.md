---
title: "thunderbird doesn't display special characters"
date: 2009-05-18
forum: General Help
---

### Post by eskararriba on 2009-05-18
hello everyone, 

I've got the following problem with thunderbird: when I get messages in german, it looks something like this: 

"werden mÃ¼ssen. Dem Missbrauch ist hier TÃ¼r und Tor geÃ¶ffnet, rechtstaatliche Kontrolle nicht vorgesehen. Die Zahlen, mit denen das Gesetz durchgedrÃ¼ckt ...."

and in other languages, like portuguese or spanish, it's the same:
 
"...famÃ*lia, porque pensam que estou no MÃ©xico. Cada e-mail Ã© uma demonstraÃ§ao muito linda de amizade e eu agradeÃ§o muito"

why is that? what can I do? in every other program, I got the fonts I need, and in thunderbird I tried every "Western" font that's available, without success. any ideas?

thanks a lot!

---

### Post by LoneWolfJack on 2009-05-18
is this from a newsletter or some automated mailing? many programmers out there STILL didn't get the idea behind the whole utf-8 thing. 

looks like you're getting an iso-8859-1 encoded email that contains utf-8 characters. you can try to copy&paste the text into gedit or OO, but afaik, there's no more practical way of dealing with this issue client-side.

---

### Post by eskararriba on 2009-05-19
it actually is from a newsletter ... well, I guess the easiest way is to open it from within gmail, then - 
thanks for your help!

---

