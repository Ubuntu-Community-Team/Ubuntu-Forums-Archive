---
title: "UTF-8 Characters aren't displayed on the virtual terminal"
date: 2008-12-10
forum: General Help
---

### Post by jessdog9001 on 2008-12-10
I'm working on some C programs that display Japanese characters on the console. All of my programs work fine in the GNOME Terminal, but when I run them on the virtual terminal (Ctrl-Alt-F1, etc.), the characters that should appear show up as rectangles. After running the unicode_start script, the characters still don't appear correctly. Strangely enough, they appear as diamonds after running the script. 

How do I get UTF-8 characters to display correctly on my terminal? Do I need to switch fonts or something? If so, how do I do that?

Here's the code for an example program that should display some Japanese characters on the screen:
```
#include <iostream>
using namespace std;
int main()
{
  cout << "&#12402;&#12425;&#12364;&#12394;" << endl;
  return 0;
}
```

---

### Post by jessdog9001 on 2008-12-17
Anyone?? I'd love to get this figured out :confused:. I'm not sure how many people run programs directly from the virtual terminal, but if I'm going to make a command line program, I'd like to know that it will work both in an X terminal as well as on the virtual terminal. If anyone has any suggestions, please speak!

---

### Post by Esthellin on 2010-05-04
I am in the same boat. I am trying to get Japanese text to display in the virtual terminals (ttys) with no luck so far. I have tried looking up a unicode console font (as console-setup only has four non-unicode fonts).

I am using Karmic by the way

---

