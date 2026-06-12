---
title: "Scripted quiz correcting progam"
date: 2008-12-12
forum: Education &amp; Science
---

### Post by Lovok on 2008-12-12
I have trouble explaining this to myself, so bear with me :)
I am wondering what would be the best programming language to accomplish this task I have in mind.
(context : weekly quizzes for grade 9-12 math)
Essentially, a program would generate a multiple choice answer style test. Each question would have randomized values, so the question may be the same on each test, but the answer would be different. The order of the multiple choices would also be randomized, so each string of answers at the end of the test would be different. 
To correct these tests, I want to be able to input the answer string into the program and have it correct for me. Each student has a different unique answer string due to the randomization. 

Basically, I want each student to have a unique test generated for them, and for the correction script to know what each test is supposed to have for answers. 

The questions will be written by myself and feature variables in them. The variables will be determined once the test is generated. The multiple choice answers will also be under variable form and fixed once the test is generated.

These tests will have to be printed to paper. So either have the program do that too, or export to a text editor to do that.	

Extra fluff : when a question is wrong, it is flagged and put on the next generated test. I also want to be able to keep track of stats and such. Maybe even have the corrector tell me "wrong" answers, "right" answers, and "misunderstood" questions. And if all goes well, maybe even automatically email the student's address with results. 

I hope my ideas were clear. If there is a better place to post this, let me know. I also willing to learn anything there is to learn programming wise.

---

### Post by rajan on 2008-12-14
one of the nice things about your problem is that there are a lot of other people that are interested in the same thing. i know of several classes that have done exactly what you're interested in. 

i am like you in that i enjoy making my own programs instead of using someone else's, but after every time i follow my folly and make a program, i find that someone else has already done it and has done a better job (you may be better than i at programming though so you may not experience this). 

some specifics to your particular problem: perl or php are great languages to know and there are lots of web scripts that run on derivatives of them.

if you are interested in running scripts that are accessible from the internet, you probably have a server in mind to host them, but not all servers will accept scripts being run on their machines. you need to know a lot of security in order to make sure your script won't expose the server to attacks. 

hope it goes well and you're right to post here. i have found this to be possibly  the most helpful place for my programming questions.

---

