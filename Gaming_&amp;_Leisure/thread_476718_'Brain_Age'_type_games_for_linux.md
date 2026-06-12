---
title: "'Brain Age' type games for linux"
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by Feba on 2007-06-17
Is there anything like this? I was thinking about creating something like it, but I can only come with ideas for games/interface/controls, I'd have no idea where to start with programming it.

---

### Post by Achetar on 2007-10-31
I was thinking of doing something like that. Only in a console and more basic.
I was thinking of something like this:

generates random number 'x' that is less than 10
generates random number 'y' that is less than 10
adds x and y to make z
output a simple math problem in the form 'x + y ='
checks your answer against z
outputs whether you got it right or wrong
repeats 30-50 times and tells you your score
score is amount_right/amount_total
asks if you want to play again


Possibly, we could add other things as separate games. And write and interface that has a list of games on the left, console in the middle\top-right, and entry area on the bottom.

I would be interested in helping on this.

---

### Post by RKCole on 2007-10-31
Achetar,

Your idea would be relatively simple in using C++.  I'm trying to update my knowledge in C++, as I'd taken and aced two C++ courses in college awhile back.  For a GUI interface wxWidgets could be used as it's free/open source.  I have the book here for wxWidgets as well...just need to get some time to study it.

C++ has a random number generator that could be used to accomplish the random numbers for x and for y.  I actually did a project for my C++ class (more of an assignment) that was quite similar to your idea.  Maybe if I get a little time I'll write up a console-based basic draft of this (if just to even try to refresh my C++ memory...haha), and I'll attach it here.  I'll see what I can do...I don't know if I could contribute too much, but maybe could give a basic foundation or something...who knows, eh?

Take care.

---

### Post by Achetar on 2007-11-01
I know, RKCole, I had the code almost done. I finished it early this morning, below there it is, and it is attached.

I am still working on having the amount of time you take affect your score...

```
#include <stdlib.h>
#include <iostream>
#include <time.h>

using namespace std;

int answer = 0;
    int x = rand()%10;
    int y = rand()%10;
    int score = 0;
    int times = 0;
    double final = 0;
    
int ask() {
    x = rand()%9;
    y = rand()%9;
    int z = x + y;
    cout << x << " + " << y << " = ";
    cin >> answer;
    if (answer == z){
               score++;
               times++;
               cout << "Right!\n";
               }
    else {
         times++;
         cout << "Wrong!\n";
         };
};

int calc_score(int score, int times) {
    final = score/times;
    final = final*100;
    return final;
};
  
int main(int argc, char *argv[])
{
    
srand(time(NULL));
    
while (times != 10){
    ask();
};
cout << "Your final score is: " << calc_score(score,times) << "\n";
cout << "Press enter to continue...";
cin >> final;
return 0;
}
```

Oh, and RKCole, believe me, you can do more than you think (i'm still a minor hehe)
BTW, I am calling this 'Brain Gain' for now

---

### Post by iperez on 2007-11-23
I'm willing to create something with a GUI, a better scoring system based on time, etc.

Your programming skills shouldn't be a problem. If you still want to do it, drop me a line at Ivan Perez <iperez@babel.ls.fi.upm.es>

---

### Post by Vadi on 2007-11-23
I'll gladly test your guys' app ;)

---

### Post by jeepee on 2008-01-22
Hey great idea. Do you guys need a neuroscientist to help with task ideas? I always wanted to make this type of game/program for linux but I don't have programming skills. However I can help with brain functions and gathering normative data, since I'm used to testing patients with cognitive deficits. jeepee2 (at) hotmail.com

Jeepee

---

### Post by iperez on 2008-01-23
Your help as neuroscientist can be extremely useful.

I created a project at sourceforge a few months ago that aims to create games for pocket pc, but these games should also work under linux, windows, etc.

If you want, we can move this conversation to that project and start deciding what kind of tests are implemented, and how the scoring system should work. Once that is done, creating the program will be much easier.

The project is located at [http://sourceforge.net/projects/pocketgames]("http://sourceforge.net/projects/pocketgames"). Tell me what you think and, if you want, join the developers mailing list there (even if you are not going to write the code).

---

### Post by mmilitia9 on 2008-01-23
Have you guys tried gbrainy?

---

### Post by iperez on 2008-01-25
Yes, I played gbrainy and had a look at the code too, and I have to say I don't like it's design (both GUI and implementation) and limitations at all.

I cannot seriously consider using gbrainy for these purposes without reimplementing it from scratch, but I will try to make this new game compatible with gbrainy's game definition format.

---

