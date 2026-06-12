---
title: "Combinatorics driving me mad"
date: 2008-06-21
forum: Education &amp; Science
---

### Post by ProbablyX on 2008-06-21
Hello!

I've been sitting here for a while trying to solve/understand a combinatorics example.

> 
I have a set with 12 elements. 

I want to create two subsets: 
* One with  6 elements 
* Another with 7 elements
* 3 elements are shared by both subsets.

In how many ways can this be done?


I've been working with this formulae, but I'm not sure it's the right one:
[IMG]http://upload.wikimedia.org/math/d/c/6/dc64c03c850bdba55990ca5e38c6263a.png[/IMG]

Like first take out 6 elements: 12!/(12-6)!
Then take out 7. The problem is that the set only has 7 elements left. So I'd have to share an element with the first subset. 
But then again three elements are to be shared.
This means that there will be elements left in the original set...

Would be great if anyone could help me :)

Thanks!

---

### Post by WW on 2008-06-21
In case this is homework, I'll just give you a hint.  You already know how to count the number of ways you can choose 6 elements from 12.  For a given choice, how many ways can you construct the second set?  You have to choose 3 from the first set (how many ways can you do that?), and 4 from the 6 that are not in the first set (how many ways can you do that?).  Multiply the three numbers together to get the total number of possibilities.

---

### Post by ProbablyX on 2008-06-21
Thanks!

I noticed that I had forgotten the X in: A!/X!(A-B)! which didn't help :)
It's not homework as such, but I do appreciate that you let me solve it myself. As I want to learn :)

Thanks a lot :D (and I suppose I shouldn't publish my solution then in case anyone else with this problem comes here)

---

### Post by mali2297 on 2008-06-22
An alternative (equivalent) solution can be obtained by reformulating the problem as [indent]*In how many ways can I partition a set with 12 elements into four disjoint subsets containing 3, 3, 4 and 2 elements respectively?*
[/indent]

Count the number of ways one can sequentially choose 3 of 12 elements, 3 of 9 elements, 4 of 6 elements and last 2 of 2 elements. Multiply.

---

