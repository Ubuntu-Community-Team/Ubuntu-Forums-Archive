---
title: "How to step back python script?"
date: 2012-05-17
forum: Education &amp; Science
---

### Post by Marcappuccino on 2012-05-17
[FONT="Georgia"]Hello,

I am much a very new user of Python, and I am trying to learn it step by step. Right now, I'm trying to create a quiz as a beginner's first program, and, I am now stuck as to how to implement some sort of loop (for/while) or a way to step back until a condition is met (the correct answer). How do I do this? :?:

Please explain in a simple way as I literally just started learning about a week ago. :) Here is the code:[/FONT]

```
question1 = "In what country does - - - live?"
answer1 = "England", "england", "Britain", "britain", "UK", "uk", "The UK", "The uk", "the uk", "United Kingdom", "The United Kingdom"
question2 = "What high school does - - - attend?"
answer2 = "School", "School #2", "School #4", "school #3"
print "Quiz"
print question1
input = raw_input ("What is your desired answer?\n>")
if input == answer1:
            print "You are right"
else:
    print "No - You are the wrong."
#This is the bit (following from here) that I am trying to do (I think it's called while loop), suggest if there is an easier way please.
while False:
             input = raw_input ("What is your desired answer?\n>")
             if input == answer1:
                 print "You are right"
             else:
                 print "Wrong again"


```

---

### Post by PeterP24 on 2012-05-18
Here is an idea:

```
question1 = "In what country does - - - live?"
answer1 = "England", "england", "Britain", "britain", "UK", "uk", "The UK", "The uk", "the uk", "United Kingdom", "The United Kingdom"
question2 = "What high school does - - - attend?"
answer2 = "School", "School #2", "School #4", "school #3"
print "Quiz"
print question1
input = raw_input ("What is your desired answer?\n>")
if input in answer1:
            print "You are right"
else:
    print "No - You are the wrong."
#This is the bit (following from here) that I am trying to do (I think it's called while loop), suggest if there is an easier way please.
while True:
             input = raw_input ("What is your desired answer?\n>")
             if input in answer1:
                 print "You are right"
                 break;
             else:
                 print "Wrong again"
```

Since answer1 and answer2 are tuples, you should not compare the input string you get returned by raw_input against them - you should check if the input is a member of your answer1 and answer2 tuples. 
Also, the while loop (and for also) loops only if the condition is True. If the condition is False, the loop body isn't executed (that was your case).  
Finally - for this kind of questions, you may want to use in the future, the appropriate section of the forum (i.e. programming talk).

---

