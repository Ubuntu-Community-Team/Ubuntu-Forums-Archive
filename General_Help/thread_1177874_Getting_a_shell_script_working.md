---
title: "Getting a shell script working"
date: 2009-06-03
forum: General Help
---

### Post by Goddard on 2009-06-03
I am trying to get a script working.  I am working on it for a class so I would like to get it myself, but nothing is working.

Here is what I have done so far.

```
m(){
mail -t $email $user -s $subject -f $file
}
```I then load the script into memory using . .myfile then

```
m mail@mail.com ccmyusername mysubject text.txt
```

It then outputs "To:" asking me who I would like to send it to.  I thought I already specified that.  I am new to shell scripting so please help me out here.

---

### Post by Goddard on 2009-06-04
I got a little closer although I am still getting CC: popping up how do I have it in the first line like so?

```
m(){
mail -t $1 -cc $2 -s $3 -f $4
}
``````
m someemail@gmail.com username what test.txt
```

---

### Post by Goddard on 2009-06-04
uhhh bump n stuff..

---

