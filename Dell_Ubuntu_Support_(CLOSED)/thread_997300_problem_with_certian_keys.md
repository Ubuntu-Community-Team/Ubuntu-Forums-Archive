---
title: "problem with certian keys"
date: 2008-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ryan6 on 2008-11-29
trying to learn shell programming and ran into a very annoying problem

i have to type the quote button twice for it to work. its the same with apostrophes, tick marks, single quotes.

that alone might not be a big deal. but i dont think they are quotes at all.

```

user@user:~/Desktop$ message=¨hello there¨
bash: there¨: command not found
user@user:~/Desktop$ message=´hello there´
bash: there´: command not found

```

it should be evaluating message literally, as a character b/c of the quotes.

```

user@user:~/Desktop$ greeting=¨hello¨
user@user:~/Desktop$ echo $greeting
¨hello¨

```

^ the quotes shouldnt be part of the variable

anyway, i have a dell inspiron e1505 laptop. it doesnt just do this in the shell, even typing this quote here --->  ¨  <--- i had to push the button twice

---

### Post by Keyper7 on 2008-11-30
I think those are not quotes. You should use the " character.

PS: it might take an entire day to check your reply to this, but I will

---

### Post by weose33 on 2008-11-30
The very creation, of pedagogy, is somewhat shielded in mystery hand now, but appears to countenance both soft of realistic grouping element. Trion is not restricting itself to games, either . With a grouping of partnerships - from strategy employment studios [buy zaishen keys](http://www.ugamegold.com/Guild-Wars-Zaishen-Keys-2995-2994-All_Servers.html)  to corporate media giants - the militia plans to do acting in not one identify of thing, but three: games, online, and conventional media (video and medium).

---

### Post by ryan6 on 2008-11-30
Keyper7, i think you hit right on my point. I dont think they are quotes either. but thats what i get when i hit the quote button twice (dont get anything when i hit it once)

i was wondering if it might just be a laptop keyboard problem, or maybe some keybinding or setup problem with linux. i dont know.

---

### Post by Keyper7 on 2008-12-01
What happens if you hit the quote button once and then another random key, like 'c'?

---

### Post by luvr on 2008-12-01
You seem to be typing the *"dead keys"*--i.e., keys that, by themselves, don't produce any visible output, but combine with other keys to produce accentuated letters. For example, a circumflex ("^") followed by a letter "a" will produce "â"; a backtick ("`") followed by a letter "e" will produce "è"; a tilde ("~") followed by a letter "n" will produce "ñ"; etc. *(To produce these so-called diacritical marks by themselves, by the way, you should type them followed by a space.)*

The 'straight apostrophies' and "straight quotes" must be present *somewhere* on your keyboard, but their exact locations depend on your keyboard layout--you may be able to produce them by holding down the <SHIFT> key and typing some number key from the top row of your keyboard; or they may sit together on one key (which will produce either one of these characters, depending on whether or not you keep the <SHIFT> key down); etc.

Really all depends on your keyboard layout.

---

### Post by jespdj on 2008-12-01
This is most likely because you have set your keyboard to **USA International**. It's a feature which makes it easy to type letters with accents like ë, é, è etc. You can type normal quotes by pressing the quotes key and then a space: " Don't press the quotes key twice, that will give you ¨ instead of " quotes.

Go to System / Preferences / Keyboard, go to the tabsheet Layouts, click Add and select USA / Default.

---

### Post by ryan6 on 2008-12-01
you guys are awesome. that problem was annoying. "check me out`' haha, thanks

---

