---
title: "Command line GREP question"
date: 2009-01-01
forum: General Help
---

### Post by Paulr-55 on 2009-01-01
This is a general question about grep, not really a "problem."

I downloaded a scrabble dictionary and I'm using grep to query for valid game words. The text file contains one word per line with no one-letter words. Yet when I do the following to get a list of 2-letter words, I get these anomalous entries:

```
paul@moonfrog:~/text/scrabble$ grep -w .. twl6.txt 
aa
ab
ad
ae
ag
ah
ahchoo
ai
al
am
an
ar
as
at
aw
ax
ay
ba
be
bi
bo
by
cornifying
de
do
ed
ef
eh
el
em
en
er
es
et
ex
fa
fe
go
ha
he
hi
hm
ho
id
if
iffier
in
is
it
jo
ka
ki
la
li
lo
ma
me
mi
mm
mo
mu
my
na
ne
no
nu
od
oe
of
oh
oi
om
on
op
or
os
ow
ox
oy
pa
pe
pi
qi
re
sh
si
so
soakage
ta
ti
to
uh
um
un
up
us
ut
we
wo
xi
xu
ya
ye
yo
za
paul@moonfrog:~/text/scrabble$ 

```

Is there something munged up in my text file or is grep malfunctioning or what? I know I can use ^..$ to get the desired results -- I just wonder what grep is doing matching ".." to "soakage" or "ahchoo".

I get a similar strange result with a search for single character words (there aren't any):

```
paul@moonfrog:~/text/scrabble$ grep -w . twl6.txt 
foraminifer
quadricepses
paul@moonfrog:~/text/scrabble$
```

I have opened and saved this text file in gvim and made a copy of it with cat but still get the same results. Any ideas?

Running 8.04 on a System76 desktop.

---

### Post by andrew.46 on 2009-01-01
Hi Paulr-55,

I can only add to the mystery as I can confirm your finding under Intrepid Ibex and GNU grep 2.5.3. But when I move to my Slackware partition the result is as it should be:

```
andrew@skamandros~/Desktop$ grep -w '..' twl6.txt 
aa
ab
ad
ae
ag
ah
ai
al
am
an
ar
as
at
aw
ax
ay
ba
be
bi
bo
by
de
do
ed
ef
eh
el
em
en
er
es
et
ex
fa
fe
go
ha
he
hi
hm
ho
id
if
in
is
it
jo
ka
ki
la
li
lo
ma
me
mi
mm
mo
mu
my
na
ne
no
nu
od
oe
of
oh
oi
om
on
op
or
os
ow
ox
oy
pa
pe
pi
qi
re
sh
si
so
ta
ti
to
uh
um
un
up
us
ut
we
wo
xi
xu
ya
ye
yo
za

```

No idea what this is about but I suspect Ubuntu? Have a look at the changelog for Intrepid grep: it is *hugely* patched:

[http://changelogs.ubuntu.com/changelogs/pool/main/g/grep/grep_2.5.3~dfsg-5ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/grep/grep_2.5.3~dfsg-5ubuntu2/changelog)

Andrew

---

### Post by Paulr-55 on 2009-01-01
Thanks for confirming that Andrew. I guess for now the -w form should be dumped in favor of the ^word$ form for this particular search under Ubuntu.

---

