---
title: "Pasting where the cursor is."
date: 2009-09-25
forum: Desktop Environments
---

### Post by bamboomy on 2009-09-25
Hi yall,

I got a question/request for feature for gnome but wanted to check whether it already exists or whether there is a reasonably simple way of achieving it.

Like most desktop users I quite regularly use the copy-paste 'feature' that is part of, well, every desktop environment I know actually. (others I don't call environments :p).

But I want to do something that would increase productivity:

You have two ways of copying in Linux, 
* select something (without further ado) and middle click on the place where you want it to be pasted
* select something, press ctrl+c and paste with ctrl+v

I want a combination of both:

I'd like to just select something and then paste it where the (keyboard) cursor is at the destination.

Middle clicking has the disadvantage that you need to place the (mouse) cursor at the place where you want it to be pasted, which is, quite often inside a large text file, while it might be handy to paste where the keyboard cursor is at the moment. Middle clicking demands that, in that case, you go exactly where the keyboard cursor is and paste it there...

I guess I'd like to have a keyboard short-cut for pasting the content of the mouse clipboard.

any suggestions?

S.

---

### Post by sweetleaf on 2009-09-25
One workaround would be to use a non-graphical text editor (nano, vi) without mouse support. Then you can middle-click anywhere in the window, and the text will paste wherever the (keyboard) cursor happens to be.

---

### Post by bamboomy on 2009-11-07
> **sweetleaf said:**
> One workaround would be to use a non-graphical text editor (nano, vi) without mouse support. Then you can middle-click anywhere in the window, and the text will paste wherever the (keyboard) cursor happens to be.

This is indeed true but also indeed a workaround...

I like to program in Java and I like doing that with eclipse.

Programming java in a non-graphical text-editor doesn't, to be polite, give as much features as eclipse. It would slow me down considerably causing the advantage of the suggested feature to be insignificant.

S.

---

### Post by sisco311 on 2009-11-07
> **bamboomy said:**
> 
I guess I'd like to have a keyboard short-cut for pasting the content of the mouse clipboard.

any suggestions?

S.

```
xsel -o
```

You may have to install xsel first.

Click [here]("apt://xsel") to install it. (apturl link)

---

### Post by bamboomy on 2009-11-07
> **sisco311 said:**
> ```
xsel -o
```

You may have to install xsel first.

Click [here]("apt://xsel") to install it. (apturl link)

If describing my problem would be a river and the solution a bridge over that river then your solution is a big run and a jump.

Although you already got halfway, you still fall into the river.

Getting the selected content of the X server to standard out is already something, but getting it into eclipse is another.

After some searching I stumbled upon glipper, it letting manage both X selection and Ctrl+c/Ctrl+v and, when the cursor is at the right place (in eclipse), clicking on the text you want to be selected in glipper and control V:

Voila :)

The content of the selected selection gets properly pasted to the place where the cursor is at the given moment...

Problem solved...

Thanks for the responses, without them I'd never have found the solution myself...

S.

---

