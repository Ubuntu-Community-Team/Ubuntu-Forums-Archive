---
title: "MIT License question"
date: 2008-01-17
forum: Education &amp; Science
---

### Post by watermark on 2008-01-17
This is a little off topic from Ubuntu, and I'm sure I'll get a bunch of IANAL, but give your thoughts anyway.

I've found javascript packages I want to use on a private site, but they are licensed under the MIT License.  I've read about it on Wikipedia, but I'm still a bit confused.

Do I just have to redistribute it if I make any changes to it?  Or is any code on the website that uses the script then subject to the same MIT license terms?  It seems to me that since javascript packages are modular, in the since I can just include them in <script> tags, I can use it with this site w/o any repercussions as long as I don't modify it...do you think this the case?

Any insight into how the MIT License might apply to javascript on a site would be great.

---

### Post by tweedledee on 2008-01-17
As I understand it, the MIT license is a ticket to do whatever you want.  And unlike the GPL, it does not influence the licensing of anything you package it with (although if you have multiple licenses, you do have to note that).  The MIT License was constructed mostly as a way of claiming original authorship, while allowing others to modify (and sell, etc.) freely.

---

### Post by Circus-Killer on 2008-01-17
ironically, today i was also wondering about the MIT license.

i was taking a look at CakePHP as a possible framework to use in the development of my companies intranet site. i'm also a bit confused about the license with regards to CakePHP.

can i freely use the CakePHP framework to develop a company site without any restrictions or major licensing concerns? is there anything i really need to know about before proceeding to use a framework that falls under the MIT license?

---

### Post by tweedledee on 2008-01-18
I am not a lawyer.... but regarding the use of CakePHP, unless the software license explicitly says something about how you can use things developed with another piece of software (in this case, your website with CakePHP), you can do whatever you like.  The MIT license does not impose any such restrictions, nor do most open-source type licenses.  The only thing you have to watch out for in development is use of libraries or other blocks of people's works you use wholesale, which may be licensed differently (this is one of the ways the GPL "contaminates" other projects, as inclusion of single GPL library mandates the GPL for the whole work, but if you develop something use a GPL tool and do not include any GPL pieces of code, you can license it however you want).

Also, one related note to the original question: I believe one restriction of the MIT license is that you can't relicense the identical body of work, i.e., you can't copy a program with an MIT license wholesale and change the license without making some of sort of change to the code.  However, the MIT license is pretty liberal, so you I may be wrong about this restriction.

---

