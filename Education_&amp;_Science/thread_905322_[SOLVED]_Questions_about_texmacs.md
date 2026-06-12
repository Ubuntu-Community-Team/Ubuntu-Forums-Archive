---
title: "[SOLVED] Questions about texmacs"
date: 2008-08-30
forum: Education &amp; Science
---

### Post by Claus7 on 2008-08-30
Hello,

In another post there was a discussion about microsoft word, wine and mathtype and that the latter didn't work so well with word. So a suggestion was to use texmacs.

I haven't used texmacs before so I would be very interested to know the following :

1)If I have a text in word with mathtype equations, and I have installed texmacs, is it possible to see that text flawlessly? (I guess not)

2)If I use texmacs to write equations can I import them to microsoft word? In other words can I use texmacs with microsoft word via wine?
And if I do so, in which format do I save the equations I have written with texmacs?

3)I think that texmacs is fully compatible with latex, so I think that I can import equations there too, am I correct?

Thank you,
Regards!

---

### Post by Vivaldi Gloria on 2008-08-30
Texmacs is not the easiest latex editor to use if you haven't used emacs before. I suggest kile, texmaker.

Actually, if you have never used latex in your life then I suggest you first try a latex based equation editor called EKEE:

[http://rlehy.free.fr/](http://rlehy.free.fr/)

Download the deb and double click to install. You can create formulas in ekee and drag them to open office. Here is a latex symbol guide which is very helpful:

[http://www.ctan.org/tex-archive/info/symbols/comprehensive/](http://www.ctan.org/tex-archive/info/symbols/comprehensive/)

If you are looking for a good latex intro see this:

[http://www.ctan.org/tex-archive/info/lshort/english/](http://www.ctan.org/tex-archive/info/lshort/english/)


> **Claus7 said:**
> 1)If I have a text in word with mathtype equations, and I have installed texmacs, is it possible to see that text flawlessly? (I guess not)

Nope. You cannot open mathtype formulas with latex.

>  2)If I use texmacs to write equations can I import them to microsoft word? In other words can I use texmacs with microsoft word via wine?
And if I do so, in which format do I save the equations I have written with texmacs?

If you use ekee then you can save the formulas as png etc. and open them with word. You can also drag formulas from ekee to open office writer. I don't know about word.

> 3)I think that texmacs is fully compatible with latex, so I think that I can import equations there too, am I correct?

I'm not sure what you mean. Texmacs is just a latex editor. You can write latex with any editor you want (including gedit, kile etc). But I think you should give ekee a try before diving into full latex.

---

### Post by Claus7 on 2008-08-30
Hello,

thank you for your answer.

So texmacs is a latex editor. I can use kile. I thought that texmacs can serce as an additional (alternative) mathtype editor where someone can write mainly mathematic equations and then upload them whenever someone liked. For example as an alternative to mathtype or to write tex equations as well. I would like to be able to :

i)see well the equations from a word text under linux via wine and
ii)to be able to write equations that I can insert to word and modify them whenever I want.

As I can see if mathtype and wine do not collaborate better there isn't any other way. 

I tried to save a texmacs equation with eps, yet it wasn't the best choise. May something else could be better for word?

Regards!

---

### Post by Claus7 on 2008-08-30
Hello,

according to this there is no solution yet.
[http://tolstoy.newcastle.edu.au/R/help/05/10/13153.html](http://tolstoy.newcastle.edu.au/R/help/05/10/13153.html)

Regards!

---

### Post by Vivaldi Gloria on 2008-08-30
You can do the things you want with ekee and OOo writer in linux. Don't know how you can transfer a formula from ekee to word in wine. In the worst case scenario you can export the formulas as (say) png from ekee and open them with word. It's really easy. Just download it and give it a try.

---

### Post by Claus7 on 2008-08-30
Hello,

thanks again for your response. I tried the ekee program both from the deb file provided and the source code. The bad thing is that for Dapper users the deb file doesn't work and the source file has many dependencies that are not satisfied easily by synaptic (I do not think that they are satisfied at all). 
With the above link and also from what I have seen is that the eps thing doesn't work either. Someone can import the eps file from word, yet the quality is very bad. Mathtype uses .eps and .wmf files more or less, yet the first doesn't work and I wasn't able to find an (equation) editor for the second type of files.
With OO the bad thing is that you cannot save an equation in such a type that it will be compatible with microsoft word. The options I get are :
odf, sxm, sfm, mml
For a check the compatible file for mw types are :
[http://support.microsoft.com/kb/290362/en-us](http://support.microsoft.com/kb/290362/en-us)

For now only the jpeg part from ekee seems to be the last resort, yet I do not know whether the quality of the equations would be good or not.

I'm changing the title in this post, because I think that it is more appropriate.

Regards!

---

### Post by Vivaldi Gloria on 2008-08-30
Attached is an ekee formula for you to try in word. Note that if you use OOo and ekee then you should be able to open them in word because the formulas are just pictures.

---

### Post by Claus7 on 2008-08-30
Hello,

about OO I didn't have the ability to save them as pictures. The equation you provide me is a very good example of what I'm looking for. The bad thing is that inserting it as picture in m word the result is that it is a little bit blurry.
Thank you. I will experiment more after I make an upgrade.

Regards!

---

### Post by Claus7 on 2008-08-31
Hello,

I tried this:
[http://ubuntuforums.org/showthread.php?t=906455](http://ubuntuforums.org/showthread.php?t=906455)

Hope this helps,
Regards!

---

### Post by xadder on 2008-09-01
Just to clear up some misunderstandings above, texmacs is *not* a LaTeX editor. It is a program inspired by LateX. It has LaTeX import and export which sometimes work, but often doesn't.

It looks like a great program, and equation writing is very fast (I prefer it to lyx for example), and LaTeX export of these quite clean. It ain't so good with figures, tables, etc.

On the other hand, it can integrate or solve equations for you (via Maxim for example), which is its real strength as far as I can see.

---

