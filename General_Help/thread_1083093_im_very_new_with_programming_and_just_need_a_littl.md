---
title: "im very new with programming and just need a little help"
date: 2009-02-28
forum: General Help
---

### Post by frog4044 on 2009-02-28
I created a small program from a guide and i can get it to run in terminal but how do i get it to become like a popup where i click the icon and it says what i told it to? When i click the icon nothing happens. 

Here is the source code

```
#include <iostream>

using namespace std;

int main()
{
cout<<"Hello world!\nhi";
cin.get();
return 1;

}
```

---

### Post by snova on 2009-02-28
> **frog4044 said:**
> I created a small program from a guide and i can get it to run in terminal but how do i get it to become like a popup where i click the icon and it says what i told it to? When i click the icon nothing happens.

You can't. It is a terminal program, thus it must be run from a terminal, otherwise its output won't go anywhere.

---

### Post by DGortze380 on 2009-02-28
> **frog4044 said:**
> I created a small program from a guide and i can get it to run in terminal but how do i get it to become like a popup where i click the icon and it says what i told it to? When i click the icon nothing happens. 

Here is the source code

```
#include <iostream>

using namespace std;

int main()
{
cout<<"Hello world!\nhi";
cin.get();
return 1;

}
```


What button are you clicking?? 

Are you using an IDE of some sort?
Did you just write it in a text file and compile with gcc?

There's nothing in that code to create a window of any kind. It outputs the string "Hello World" to the standard out (terminal screen). So I'm confused when you say;

> **frog4044 said:**
> When i click the icon nothing happens. 


Also, typically main should return 0. Not necessarily required, but still a common convention.

---

