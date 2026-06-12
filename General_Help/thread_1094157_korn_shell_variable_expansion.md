---
title: "korn shell variable expansion"
date: 2009-03-12
forum: General Help
---

### Post by BradleyAtkins on 2009-03-12
Hi all

Just made the embarrassing discovery while debugging a script that I don't actually understand korn shell variable expansion.

I had always thought that to use the value of a variable you needed to expand it by prefixing it with a $. However: -

/home/brad>x=10;y=8
/home/brad>[[ x -gt y ]] && echo yes
yes
/home/brad>[[ x -gt $y ]] && echo yes
yes

/home/brad>x=10;y=88                
/home/brad>[[ x -gt y ]] && echo yes
/home/brad>
 
Plainly the test is happy to use the values of x and y with or without the $ expansion. It seems you only need to expand it when you want to echo it out to something: -

/home/brad>printf "%d\n" x
10
/home/brad>echo x
x

Yet all of the tutorials and books I read on the korn shell are emphatic that you need the $ expansion to access the value of the variable.

Can anyone enlighten me further?

Brad

---

