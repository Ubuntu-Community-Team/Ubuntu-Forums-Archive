---
title: "How to enable autocompletion of whitespaces in terminal?"
date: 2008-12-12
forum: General Help
---

### Post by darthmob on 2008-12-12
I have got a rather simple but annoying problem when working with the gnome terminal in folders with whitespaces.

an example directory:
/home/darthmob/diary/day\ 5/

normally when I *cd* into such folders it should automatically add the '\ ' when pressing tab. interestingly it does not work anymore on both my desktop computer and my notebook. when I press tab now it completes until *day* and I have to type both backslash and number by hand. in addition it clears the already typed backslash when pressing tab a second time.

I'm using ubuntu 7.10 and 8.04 with the default gnome terminal (which is the bash?!) on openbox/gnome.

anyone involved with successfully solving that mystery will get a nice cookie! :)


**/edit:**
it embarasses me a bit to confess that I solved the not so mysterious mystery. the terminal does not autocomplete whitespaces if there is an equally named folder without whitespace. for example:

/day1
/day\ 2
/day\ 3

it works well if I type 'day\ ' and press tab. I think the case is solved and can be closed.
I have attached some cookies as promised!

---

### Post by iponeverything on 2008-12-12
so your saying it used to go to 

"/home/darthmob/diary/day\ "

and now only goes to:

"/home/darthmob/diary/day"

As an test:

```
mkdir test
cd test
mkdir "foo bar"
cd <tab>
cd ..
mkdir "foo baz"
cd <tab> <tab>
mkdir "foo_foo"
cd <tab>

```

---

### Post by darthmob on 2008-12-13
as I added in the edit it was never really broken. my clean folder structure was simply not as clean as I thought. ;)

in your example: it does not autocomplete beyond the point where names change which is the normal behaviour. you have to type '\ ' manually and than it completes the folders with whitespaces in it.

---

