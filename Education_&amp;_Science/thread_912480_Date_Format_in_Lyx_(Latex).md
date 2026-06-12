---
title: "Date Format in Lyx (Latex)"
date: 2008-09-06
forum: Education &amp; Science
---

### Post by gmjs on 2008-09-06
Hi,

I wanted to change the format of the date printed in a Lyx document using the **\today** latex command.  The default format is **7th September 2008** and I wanted **07/09/2008** instead.

I thought that this might be quite straight forward, but apparently it isn't.

I found a package called **datetime** that lets you alter the format of the date that **\today** returns.  So at the moment, I'm using:

```
\usepackage[british]{babel}
\usepackage{datetime}

\ddmmyyyydate \today
```

This does work but it's not exactly 'computer-y' is it?

Does anyone know of a better way to specify a date format that's more flexible (i.e. does not require its own function, but can be chosen using placeholders - e.g. %d/%m/%Y).

The Lyx date format option **Tools > Preferences > Outputs > Date format ** doesn't make a difference to the output of **\today**.

Any help greatfully appreciated.

Graham

---

### Post by Vivaldi Gloria on 2008-09-07
> **gmjs said:**
> \usepackage{datetime}
\ddmmyyyydate \today[/code]

> Does anyone know of a better way to specify a date format that's more flexible (i.e. does not require its own function, but can be chosen using placeholders - e.g. %d/%m/%Y).

I can't see a big difference between "\ddmmyyyydate" and "%d/%m/%Y". It looks like the first even has a better control over digits. I don't understand why you are not happy with it.

---

### Post by gmjs on 2008-09-08
I know - I'm very picky!

It just seems strange that it's easier to use a command defined by someone else in a package file specifically for that date format, rather than there being a package that lets you adjust the date format on the fly.

I don't suppose it's going to happen, but if I wanted the date in the format "08/Sep/2008" or "Monday 8th September 08", I should be able to specify it, rather than relying on someone (a lot better at programming than me :D) to code a specific command for it.

I just wanted to be sure I wasn't overlooking something.  It'd be just my luck if you could put something like \date[dd/mm/yyyy]{\today} instead, but just didn't know about it!

I know - get a life Graham - there are much more important things to worry about.  It's what Linux is all about though - right! ;)

Thanks for the reply though!

Graham

---

### Post by Vivaldi Gloria on 2008-09-08
> **gmjs said:**
> It'd be just my luck if you could put something like \date[dd/mm/yyyy]{\today} instead, but just didn't know about it!

I know - get a life Graham - there are much more important things to worry about.  It's what Linux is all about though - right! ;)

Thanks for the reply though!

Graham

Good find / right / You're welcome / Cheers. :-)

---

### Post by srharriott on 2009-09-14
I'm writing a letter in TeX and the the date is automatically produced and displayed in an American format as "September 14, 2009".

I need it in an English format, so added the following code:

```

\usepackage[british]{babel}
\usepackage{datetime}

```

The date is now displayed as "Monday 14 September, 2009".

Does anyone know how to get rid of the day, so the date reads "14 September, 2009", without having to enter it manually?

Thanks, Ste.

---

### Post by gmjs on 2009-09-14
Hello,

To remove the day of the week, you can use the following package option-- 'nodayofweek'.

To use a latex package option, you enter it in square brackets after the \usepackage declaration.  For example:

```
\usepackage[british]{babel}
\usepackage**[nodayofweek]**{datetime}

\longdate{\today}

```

Hope this helps.

Graham

---

### Post by srharriott on 2009-09-15
Yea, that did it.

Thank you.

---

### Post by Xnst on 2009-09-21
Hi gmjs,

I am glad to see that it is not just me that is pecky:)

I tried to express the date as the Swedish standard suggests and ended up with:

```

\usepackage{datetime}
\renewcommand{\dateseparator}{-}
\newcommand{\todayiso}{\the\year \dateseparator \twodigit\month \dateseparator \twodigit\day}

```

I hope some help comes from this.

---

### Post by gmjs on 2009-09-21
Brilliant--exactly the control I wanted over dates in LaTeX!

Many thanks!

Graham

---

### Post by AlanQ on 2010-01-07
Just what I was looking for too :) Thank you to all.

One question for Xnst:
Why is it '\the\year' and not just '\year' ?

I tried finding the answer myself but Google search throws away '\'s
and I'm not sure what else to search on.

I'd be grateful if someone could point me towards a reference that explains *modifiers* like '\the' and '\twodigit'.
There's no mention of '\the\year' (or '\the\*anythingelse*') in the datetime package pdf ([http://mirror.ctan.org/macros/latex/contrib/datetime/datetime.pdf](http://mirror.ctan.org/macros/latex/contrib/datetime/datetime.pdf)).

Cheers
Alan

---

### Post by Xnst on 2010-01-08
Hi AlanQ,

I am sorry :( I cannot answer your question. I think I found the sequence somewhere on the net ( Would have been nice with a reference here, but I forgot where I found it, sorry!)  The best thing I guess would be to write to Nicola Talbot who wrote the datetime package. 

But, I see in the datetime.pdf that I could have done the code better by using \newdateformat in the datetime.cfg file.  Perhaps, in some future, I will  :)

---

### Post by AlanQ on 2010-01-08
Hello Xnst

Thank you for your reply.

> I am sorry I cannot answer your question. I think I found the sequence somewhere on the net ( Would have been nice with a reference here, but I forgot where I found it, sorry!) The best thing I guess would be to write to Nicola Talbot who wrote the datetime package.

I'm actually looking for a more general explanation of how commands can be modified by putting other commands in front of them, viz [FONT="Courier New"]\modifier\command[/FONT].
But I might write to Nicola anyway just to tell her how brilliant I think the datetime package is :)

> But, I see in the datetime.pdf that I could have done the code better by using \newdateformat in the datetime.cfg file. Perhaps, in some future, I will 

So Latex even allows system wide user configuration files.
The more I play with Latex the more I like it!

Cheers
Alan

---

