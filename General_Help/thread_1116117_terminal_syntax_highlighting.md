---
title: "terminal syntax highlighting"
date: 2009-04-04
forum: General Help
---

### Post by Isomorphismus on 2009-04-04
Hi! 
I remember to have seen on one linux -computer, that in the terminal the line user@hostname was coloured green - is this possible in ubuntu? it would be much easier to find the last command I typed if it was coloured...

thx,
Iso

---

### Post by lloyd_b on 2009-04-05
To get that green prompt, edit the file "~/.bashrc", and remove the "#" from the beginning of the line ```
#force_color_prompt=yes
```

For more info on customizing the prompt, [read this]("http://www.ibm.com/developerworks/linux/library/l-tip-prompt/")

Lloyd B.

---

### Post by Isomorphismus on 2009-04-05
thanks!

---

### Post by chamarams on 2009-04-06
please understand my problem i am student and i am new to programing.while i am writting code isn't help colour hilighting like below...i want activate it...i am writting code ubuntu terminal



[COLOR="DarkOrchid"]#include[/COLOR][COLOR="Magenta"]<iostream>[/COLOR]
[COLOR="DarkRed"]using namespace[/COLOR] std;
[COLOR="DarkGreen"]int[/COLOR] main()
{
cout<<[COLOR="Magenta"]"chamara"[/COLOR]<<endl;


[COLOR="DarkRed"]return[/COLOR] [COLOR="Magenta"]0[/COLOR];
}

---

### Post by ryanhaigh on 2009-04-06
> **chamarams said:**
> please understand my problem i am student and i am new to programing.while i am writting code isn't help colour hilighting like below...i want activate it...i am writting code ubuntu terminal

What editor are you using. I have syntax highlighting for a number of languages/file types just by uncommenting the associated lines in /etc/nanorc. Obviously this only applies to nano.

---

### Post by mb_webguy on 2009-04-06
Code highlighting isn't the same as what the OP was asking, and to my knowledge isn't available in any terminal text editor.  It is, however, available in many GUI text editors including Gedit (the default Ubuntu text editor) and Kate (the default Kubuntu text editor), as well as the numerous available IDEs such as NetBeans, Code::Blocks, KDevelop, and MonoDevelop.

---

### Post by ryanhaigh on 2009-04-07
That example the OP has presented looks a lot like code highlighting to me. Furthermore code highlighting is available in terminal based text editors, somehow I don't think Emacs and Vim would have the crazy level of devotion they command without having this as one (of their very very many) features.

---

### Post by mb_webguy on 2009-04-07
> **ryanhaigh said:**
> That example the OP has presented looks a lot like code highlighting to me. Furthermore code highlighting is available in terminal based text editors, somehow I don't think Emacs and Vim would have the crazy level of devotion they command without having this as one (of their very very many) features.

The OP was asking about a colored prompt, which isn't quite the same as syntax highlighting.

However, I stand corrected about terminal-based editors being capable of syntax highlighting.  A bit of research turned up a few useful references...

[Nano Syntax Highlighting]("http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting#Syntax_Highlighting_Code")
[Vim documentation: syntax]("http://vimdoc.sourceforge.net/htmldoc/syntax.html")

In my defense, the last time I used terminal-based editors for coding was back about twelve years ago when I was using telnet to connect to an AIX mainframe...  Back then, color prompts and syntax highlighting were almost cutting-edge technology.  ;)

---

### Post by ryanhaigh on 2009-04-07
I too stand corrected, the OP I was talking about was in fact not the OP at all, I was responding to chamarams post.

---

