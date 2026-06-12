---
title: "Computing Sine"
date: 2009-04-28
forum: Education &amp; Science
---

### Post by GTyron on 2009-04-28
I've been having trouble with an assignment to compute the sine of an angle. We have to write our own function rather than use the one in the standard math library. For the most part I have it but, it seems I am having some trouble understanding the formula given:

   Sin( x ) = x – x3/3! + x5/5! – x7/7!


My code:
double sin(float angle) {

    int add = 1;
    long double radian = angle * PI / 180.0;
    long double previousX;
    long double x = radian;
    long long i = 3;
    long double diff;

    do {
        previousX = x;
        //NARROWED PROBLEM DOWN TO HERE
        if (add = !add) {
            x =+ (power(radian, i) / i);
        } else {
            x =- (power(radian, i) / i);
        }
        //END PROBLEM SECTION
        i += 2;
        if (x > previousX) {
            diff = x - previousX;
        } else {
            diff = previousX - x;
        }

    } while (diff > 0.00000001);
            x = radian - (power(radian, i) / i);
    return x;
}

---

### Post by ssam on 2009-04-29
> **GTyron said:**
> 
        //NARROWED PROBLEM DOWN TO HERE
        **if (add = !add)** {
            x =+ (power(radian, i) / i);
        } else {
            x =- (power(radian, i) / i);
        }
        //END PROBLEM SECTION


this is an assignment, so i can't give you all the answers

```
if (add = !add)
```
means
"if add does not equal add"
add does equal add (they are the same), the that if clause is always false.

is that enough to get you going?

PS:
5! means 5x4x3x2x1 [http://en.wikipedia.org/wiki/Factorial](http://en.wikipedia.org/wiki/Factorial)

PPS:
when you code is not doing what you expect put in cout or printf statements, to output the variables a various places. for example print out x, i and add at each run of the loop.

---

### Post by GTyron on 2009-04-29
The if else structure as I designed it works fine, it's the body of the structures that evidently have an issue. 

if (add = !add) changes the value of add from false to true or from true to false each round so that it executes each line every other round through the loop. I'm simply changing it while evaluating it.

Though I believe what you told me regarding the factorial will fix my problem, thank you.

---

### Post by ssam on 2009-04-30
> **GTyron said:**
> The if else structure as I designed it works fine, it's the body of the structures that evidently have an issue. 

if (add = !add) changes the value of add from false to true or from true to false each round so that it executes each line every other round through the loop. I'm simply changing it while evaluating it.

Though I believe what you told me regarding the factorial will fix my problem, thank you.

oops, my bad. i read it as ```
if (add != add)
```.

C is so sneaky.

---

### Post by jbrefort on 2009-05-02
Looks like you are dividing by i instead of !i.

---

### Post by lisati on 2009-05-02
> **ssam said:**
> oops, my bad. i read it as ```
if (add != add)
```.

C is so sneaky.

I read it as if it was  ```
if (add == !add)
```

Ooops.

---

