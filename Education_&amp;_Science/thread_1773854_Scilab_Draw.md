---
title: "Scilab Draw"
date: 2011-06-02
forum: Education &amp; Science
---

### Post by AschenStrom on 2011-06-02
Hello 
i've got a problem that you may help me to solve.
i'm a student and this year has been full of exams. I've studyied so much for all my courses that i didnt find much time to learn scilab. Unluckly i've a little "homework" to do using scilab so, i'm studying how to use this program and all his commands. The time isn't much and i still have some other exam to complete and i can't really spend to much time on this very little homwork that, anyway, it's necessary.
I don't hope to receive the complete homework from you but, i'll apreciate much any kind of help that you can give to me. 
 
what i've to do is a little draw of something... that seems easy, but i cant manage to do it.
if someone is able to make it, or just a part, i'll need also some instruction with // that explain me what you have done because i'm planning to learning how to use scilab also if this will be the only one thing that i've to do with scilab into my courses.
 
thank you very much
 
here there is an exemple. 
[IMG]http://img199.imageshack.us/img199/6702/immagineavk.jpg[/IMG]

---

### Post by PeterP24 on 2011-06-02
I believe you need the xpoly() function. Here is something to get you started: 

```
// A little program which draws a shape similar to the 'F' character
// The letter thickness is 2, its height is 10 and its width is 8. 
// The middle part width is 6

// Here are the dots defining the corner points of the "F" shape
        
points=[0  0  8 8 2 2 6 6 2 2
        0 10 10 8 8 6 6 4 4 0]; // on the upper row - x coords; the second row - y coords

plot2d(0,0,-1,"010"," ",[-1,-1,10,12]); // Create an empty canvas with specified dimensions (by the last vector)
                                        // it also draws the 0, 0 point (you'll see a cross marking the point - but you can use plot2d to specify other 
                                        //points - for example two points marking the dogs eyes with the appropriate marks)

xpoly(points(1, :), points(2, :),"lines",1); // taken from the example (search help xpoly). Actually using this
                                             // function you can draw any 2D design provided that you need only 
                                             // straight segments not curves and that you know the points defining
                                             // your shape
                             
// In case you need to open the shape (the contour is by default closed):
// obtain a handle to the mentioned polyline (the handle is an integer which
// uniquely identifies the polyline)
// use the handle to modify the options provided in the help example (again see xpoly on the help browser - this code snippet is inspired by it)
                                             
```

You should study the example from the help (type help xpoly at the scilab prompt) to see for example how to open the contour (it is closed by default). Also you may want to check the help to see other way to do it. As a personal thought - right now I don't see the educational value of your assigned homework so may I ask what is the name of the class you take? (in which you need to do this assignment)

pts

---

### Post by AschenStrom on 2011-06-03
thanks for you help. 
 
i'm studying design and i have a a math exam with 3 tests. I've passed 2/3 of them but, in the program, i've also scilab... and last year was matlab lol... so i dont really understand what's the educational value me too... but i have to do it :(
maybe this is intended to be an help for a future course with maya (that i've already passed).
 
i'll try to start with your guide
and sorry for my bad english
 
thanks again

---

