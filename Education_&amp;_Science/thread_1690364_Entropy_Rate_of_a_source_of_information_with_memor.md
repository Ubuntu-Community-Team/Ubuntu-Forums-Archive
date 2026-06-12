---
title: "Entropy Rate of a source of information with memory"
date: 2011-02-18
forum: Education &amp; Science
---

### Post by matrronchi on 2011-02-18
Hey there!

I'm studying information theory and was wondering if any one of you had an idea about how to calculate the entropy rate of a source of information with memory.

For example, if i have some text written in English i can easily calculate it's entropy by knowing the medium frequencies of each of the alphabet's letter.

H(text) = sum_on_all_letters(-log2(probability_of_each_letter) * (probability_of_each_letter))

However when the source is with memory we can do better than entropy...
We can reach the entropy rate of that source of information, which is defined as  the limit of the joint entropy of n dipendent sources deriving from the original one, diveded by n when n goes to infinity..

(sorry if i was a little confusying in giving definitions...check wiki for better ones ;D)

now my question is..

How would you calculate the entropy rate of english language??
Does anybody have an idea of an algorithm or pseudocode that could calculate it?

I think i should calculate relative probabilities between occurencies of different letters one close to another..am i right?

Thanks guys...

---

### Post by azim.charaniya on 2011-06-01
it is calculated by the formula 
           M
[SIZE=4]H=-[IMG]http://upload.wikimedia.org/math/3/d/a/3da6e77cca6c503ce2bdbdc702e182f0.png[/IMG]P[/SIZE]k[SIZE=4]log[/SIZE]2[SIZE=4]P[/SIZE]k
           K=1

unit is bits/message
Pk are the probability of the message Qk to occur

I am studying the same 
bit confused in Information Rate  Part

---

