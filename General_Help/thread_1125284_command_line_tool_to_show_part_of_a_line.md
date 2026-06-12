---
title: "command line tool to show part of a line"
date: 2009-04-14
forum: General Help
---

### Post by geo909 on 2009-04-14
Hello all,

in some scripts, I occasionally need to manipulate a part of a line (usually an output of some command). I was wondering how could I do 
the following with a line (well, that would be just a string, but containing spaces as well)

1) Display characters from m to n for some numbers m<n.
For example, if we have the line "hello, I am a string",
characters from 4 to 15 will be: "lo, I am a s"

2) Display word number n. That is, in the above sentence,
word number 2 will be "I", word number 5 will be "string" etc

Is there any simple way in bash to do those two things?

Thanks a lot in advance..

---

### Post by askreet on 2009-04-14
You're beginning to enter the wonderful world of *nix commandline!

There are so many tools to do what you want, here's some examples:

cut, to get certain characters:

laptop% echo "hello, I am a string"| cut -c4-15  
lo, I am a s

cut, to get certain fields using space as a delimiter:
laptop% echo "hello, I am a string"| cut -d' ' -f2
I
laptop% echo "hello, I am a string"| cut -d' ' -f5
string

awk, for better field matching.  awk has a better understanding of variance in field output, for example the output from "df", which uses padding spaces to align fields.  Using cut -d' ' would result in lots of empty fields and inconsistant field numbering, but awk is a champ:

original output:
laptop% df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3              8924700   4605176   3866092  55% /
tmpfs                  1035616         0   1035616   0% /lib/init/rw
varrun                 1035616       344   1035272   1% /var/run
varlock                1035616         0   1035616   0% /var/lock
udev                   1035616      2980   1032636   1% /dev
tmpfs                  1035616       460   1035156   1% /dev/shm
lrm                    1035616      2004   1033612   1% /lib/modules/2.6.27-11-g

Lets clean it up with some awk:
ksmith-laptop% df|grep -v Filesystem|awk "{ print \$1,\$5 }"
/dev/sda3 55%
tmpfs 0%
varrun 1%
varlock 0%
udev 1%
tmpfs 1%
lrm 1%

You'll notice I threw a grep -v in there to get rid of lines containing Filesystem, didn't want that nasty header line sticking around!

I hope this gets you started to mastering one-liners and the like.  Be sure to read the man pages for sed, awk, cut, sort, uniq.

Once you get them all you can do some crazy stuff like this:

cat access.log|awk "{ print \$11 }"|sort|uniq -c |sort -nr|head

^-- one-liner to get the top 10 requested URIs from an apache access log :)

HTH,
askreet.

---

### Post by Claus7 on 2009-04-14
Hello &#967;&#945;&#943;&#961;&#949;&#964;&#945;&#953;!, 

have you concidered using awk? That way you will be able to treat columns by $x, where x is the number of column you wich to print. Awk is an excellent tool for manipulating text data. I would advice you to install it from synaptic as gawk, which is a flavour of awk. 

For example if you want from a file the third column you can type:
awk '{print $3}' inputfile > outputfile 

You can use also the cut command selecting columns with the -f option.

edit: @askreet:very detailed explanation!

Regards &#967;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;!

---

### Post by lloyd_b on 2009-04-14
For the first case, the simplest solution is to use bash's inbuilt string handling - using the format "${VAR:Start:Length}".  For Example:```
TEST="hello, I am a string";echo ${TEST:4:11}
```

Lloyd B.

---

### Post by geo909 on 2009-04-14
Thanks for the feedback guys!! 

I have more than enough to do my job now. And it was nice to see several tools.

Btw, where did the "say thank you" button go?! It's been some time since it disappeared or is some issue with my browser (?!?)



P.S. &#915;&#949;&#953;&#940; &#963;&#959;&#965; &#966;&#943;&#955;&#949; Claus7, are you greek or you just know the greetings?!

---

### Post by Claus7 on 2009-04-14
Hello,

> **geo909 said:**
> 
P.S. &#915;&#949;&#953;&#940; &#963;&#959;&#965; &#966;&#943;&#955;&#949; Claus7, are you greek or you just know the greetings?!

[based on the question I decided to answer in the hellenic language]

&#915;&#949;&#953;&#945; &#963;&#959;&#965; &#961;&#949; &#922;&#961;&#951;&#964;&#953;&#954;&#941;!

&#934;&#945;&#957;&#964;&#940;&#950;&#959;&#956;&#945;&#953; &#956;&#949;&#964;&#940; &#945;&#960;&#972; &#945;&#965;&#964;&#972; &#957;&#945; &#941;&#967;&#949;&#953;&#962; &#954;&#945;&#964;&#945;&#955;&#940;&#946;&#949;&#953; &#960;&#949;&#961;&#943; &#964;&#943;&#957;&#959;&#962; &#960;&#961;&#972;&#954;&#949;&#953;&#964;&#945;&#953;...

&#914;&#940;&#963;&#949;&#953; &#964;&#951;&#962; &#949;&#961;&#974;&#964;&#951;&#963;&#942;&#962; &#963;&#959;&#965;, &#957;&#945; &#963;&#959;&#965; &#960;&#969; &#972;&#964;&#953; &#956;&#960;&#942;&#954;&#945; &#954;&#945;&#953; &#947;&#969; &#955;&#943;&#947;&#959; &#963;&#964;&#959; &#968;&#940;&#958;&#953;&#956;&#959; &#974;&#963;&#964;&#949; &#957;&#945; &#946;&#961;&#969; &#954;&#940;&#960;&#959;&#953;&#945; &#960;&#961;&#945;&#947;&#956;&#945;&#964;&#940;&#954;&#953;&#945; &#954;&#945;&#953; &#957;&#945; &#963;&#959;&#965; &#945;&#960;&#945;&#957;&#964;&#942;&#963;&#969;. &#915;&#953;&#945; &#964;&#953;&#962; &#963;&#964;&#942;&#955;&#949;&#962; &#956;&#949; &#964;&#959; awk &#949;&#943;&#957;&#945;&#953; &#949;&#973;&#954;&#959;&#955;&#959; &#963;&#967;&#949;&#964;&#953;&#954;&#940;. &#932;&#953;&#962; &#960;&#949;&#961;&#953;&#963;&#963;&#972;&#964;&#949;&#961;&#949;&#962; &#966;&#959;&#961;&#941;&#962; &#945;&#965;&#964;&#972; &#960;&#959;&#965; &#963;&#959;&#965; &#941;&#947;&#961;&#945;&#968;&#945; &#963;&#949; &#954;&#945;&#955;&#973;&#960;&#964;&#949;&#953;. &#932;&#959; &#952;&#941;&#956;&#945; &#949;&#943;&#957;&#945;&#953; &#957;&#945; &#949;&#960;&#953;&#955;&#941;&#958;&#949;&#953;&#962; &#941;&#954;&#964;&#945;&#963;&#951; (range) &#954;&#945;&#953; &#957;&#945; &#963;&#964;&#959; &#964;&#965;&#960;&#974;&#963;&#949;&#953; &#963;&#949; &#956;&#953;&#945; &#947;&#961;&#945;&#956;&#956;&#942;. &#924;&#949; &#941;&#957;&#945; for loop &#964;&#951;&#957; &#954;&#940;&#957;&#949;&#953;&#962; &#964;&#951; &#948;&#959;&#965;&#955;&#949;&#953;&#940; &#963;&#959;&#965;, &#945;&#955;&#955;&#940; &#963;&#964;&#945; &#964;&#965;&#960;&#974;&#957;&#949;&#953; &#954;&#940;&#952;&#949;&#964;&#945;. &#934;&#945;&#957;&#964;&#940;&#950;&#959;&#956;&#945;&#953; &#972;&#964;&#953; &#952;&#945; &#942;&#952;&#949;&#955;&#949;&#962; &#959;&#961;&#953;&#950;&#972;&#957;&#964;&#953;&#945;. &#917;&#948;&#974; &#954;&#945;&#953; &#956;&#949; &#964;&#953;&#962; &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#960;&#959;&#965; &#963;&#959;&#965; &#949;&#943;&#960;&#945;&#957; &#964;&#945; &#960;&#945;&#953;&#948;&#953;&#940;, &#972;&#960;&#969;&#962; &#949;&#943;&#960;&#949;&#962;, &#952;&#945; &#941;&#967;&#949;&#953;&#962; &#945;&#961;&#954;&#949;&#964;&#972; &#965;&#955;&#953;&#954;&#972; &#947;&#953;&#945; &#960;&#949;&#953;&#961;&#945;&#956;&#945;&#964;&#953;&#963;&#956;&#972;.

> **geo909 said:**
> Btw, where did the "say thank you" button go?! It's been some time since it disappeared or is some issue with my browser (?!?)

There is no issue with your browser. For some time now, the users have not that ability as they used to have to mark their threads as solved and to be able to thank other users via the thanks button. That is, so as to enable better server performance for the ubuntu forums (if I have understood correctly).

&#935;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;, &#954;&#945;&#955;&#942; &#963;&#965;&#957;&#941;&#967;&#949;&#953;&#945; -Regards-!

---

### Post by geo909 on 2009-04-15
&#935;&#945;&#967;&#945;, &#947;&#949;&#953;&#940; &#963;&#959;&#965; bre &#963;&#973;&#957;&#964;&#949;&#954;&#957;&#949;!! Don't do any further searching, as I said I have more than enough now.. Thanks a lot for your time, I appreciate it!

> There is no issue with your browser. For some time now, the users have not that ability as they used to have to mark their threads as solved and to be able to thank other users via the thanks button. That is, so as to enable better server performance for the ubuntu forums (if I have understood correctly).


Oh well.. The "thanks" option was a (stupid!) motivation for people to try to give more answers. I have seen people asking for thanks in their signature if their answers are proven to be helpful (a big "*get a life*" to them)! But the 'solved' option was quite helpful; sometimes it takes a while to realize if the issue arised in a big thread is solved or not. Anyway.


                      Regards
                            &#915;&#953;&#974;&#961;&#947;&#959;&#962;

---

### Post by andrew.46 on 2009-04-15
Hi,

It is no help to your specific needs but try the following:

```
echo 'hello, I am a string' | rev
```

How cool is that! One day perhaps I will find a use for this little utility in a script :-).

Andrew

---

