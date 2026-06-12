---
title: "/usr/share/info/coreutils.info.gz to .doc or .txt ???"
date: 2009-04-16
forum: General Help
---

### Post by Will4 on 2009-04-16
hey guys,

I need to have the output of the command 

> sudo info core util

into a .txt or .doc or any text format to have it read later and learn from it. Can anyone help me please. I am not acquainted with "info" command so i don't know how to output it to a text document. 

Any help???

---

### Post by ostrm on 2009-04-16
First of all, there is no node "util" in the info pages of core...

You can use the option -o [filename] to output the contents to a file. The following will redirect the info output of coreutils including all the subnodes (note the --subnodes switch, I guess this is what you need) to info.txt

```

info --subnodes -o info.txt core

```

---

### Post by Will4 on 2009-04-16
if that is, how can i find later the info.txt ?? where does it ends up?? Sorry, i'm a dummy user, hehe

---

### Post by ostrm on 2009-04-16
The file is going to be saved in the current directory you are in. So if your command line looks like this 
```
hero@dungeon /home/hero $ info --subnodes -o info.txt core
```
before executing the command, info.txt will end up in your home.

You can also give the full path like in ```
hero@dungeon /home/hero $ info --subnodes -o /home/hero/learnsomething/info.txt core
```

and the file will be in the subdirectory "learnsomething" of your home.

---

### Post by Will4 on 2009-04-16
Thank you Ostrm,

I did what you said and got nothing but an endless .txt with this 

> &#2599;††&#20512;&#26994;&#29806;&#24864;&#29984;&#24947;&#25959;&#27936;&#29541;&#24947;&#25959;&#27680;&#29545;&#26996;&#26478;&#24864;&#27756;&#24864;&#24950;&#27753;&#25185;&#25964;&#28448;&#29808;&#28521;&#29550;&#8236;&#26740;&#28261;&#25888;&#27000;&#2676;††&#29472;&#25461;&#25955;&#29555;&#30054;&#27756;&#11897;&#2570;&#11616;&#30253;&#29285;&#26995;&#28271;&#2599;††&#20512;&#26994;&#29806;&#29728;&#25960;&#30240;&#29285;&#26995;&#28271;&#28192;&#28021;&#25954;&#11378;&#29728;&#25960;&#8302;&#30821;&#29801;&#29472;&#25461;&#25955;&#29555;&#30054;&#27756;&#11897;&#2570;&#11616;&#10029;&#8202;††&#25924;&#26988;&#26989;&#8308;&#26740;&#8293;&#28783;&#26996;&#28271;&#27680;&#29545;&#11892;†&#24908;&#25972;&#8306;&#29281;&#30055;&#25965;&#29806;&#11379;&#26912;&#8294;&#28257;&#11385;&#24864;&#25970;&#29728;&#25970;&#29793;&#25701;&#24864;&#2675;††&#28448;&#25968;&#24946;&#25710;&#8307;&#30309;&#28261;&#26912;&#8294;&#26740;&#31077;&#25120;&#26469;&#28265;&#30496;&#29801;&#8296;&#11616;&#11815;†&#28486;&#8306;&#30821;&#28001;&#27760;&#11365;&#24608;&#28531;&#29810;&#11552;*&#29229;&#2599;††&#29216;&#24933;&#29540;&#26144;&#28530;&#8301;&#26740;&#8293;&#26982;&#25964;&#28192;&#28001;&#25701;&#24608;&#29229;&#11815;&#2570;&#8202;†&#8257;&#26995;&#26478;&#25964;&#24608;&#10029;&#28448;&#25968;&#24946;&#25710;&#26912;&#8307;&#28526;&#8308;&#25970;&#27745;&#31084;&#24864;&#8302;&#28783;&#26996;&#28271;&#8236;&#26740;&#30063;&#26727;&#26912;&#8308;&#28524;&#27503;&#8307;&#26988;&#25963;&#28426;&#25966;*&#18720;&#8308;&#29811;&#28257;&#29540;&#26144;&#29295;&#29472;&#24948;&#25710;&#29281;&#8292;&#28265;&#30064;&#11380;&#28448;&#8306;&#28518;&#8306;&#29811;&#28257;&#24932;&#25714;&#28448;&#29813;&#30064;&#8308;&#26217;&#29728;&#24936;&#8308;&#29545;&#25354;&#25964;&#29281;&#26144;&#28530;&#8301;&#26740;&#8293;&#28515;&#29806;&#30821;&#11892;†&#28486;&#8306;&#30821;&#28001;&#27760;&#11365;&#24608;&#28531;&#29810;&#11552;&#8231;&#25970;&#25697;&#8307;&#29286;&#28015;&#29472;&#24948;&#25710;&#29281;&#2660;&#28265;&#30064;&#11380;&#24864;&#25710;&#26912;&#8307;&#29029;&#26997;&#24950;&#25964;&#29806;&#29728;&#8303;&#27760;&#26977;&#8302;&#29536;&#29295;&#10100;&#8236;&#28257;&#8292;&#29792;&#25957;&#11552;&#8231;

Sorry, this is all i got. The whole .txt is like this. Any idea?? how can we succeed??? 
Thank you !!!

---

### Post by Will4 on 2009-04-17
Any Idea on how to solve this problem??
is a font-code problems right??

Help please!!

---

### Post by ostrm on 2009-04-17
You are not Chinese, are you? :-)

Do you get the same output if you just run "info core"?
Please post the output of "locale".

---

### Post by Will4 on 2009-04-21
No, I'm not chinese!! hahaha

Ok, i did 
info --subnodes -o info corestill the same result

no way i can get it in English!! 
any idea??

---

