---
title: "Konsole New Screen Session always shows credits"
date: 2006-02-15
forum: Desktop Environments
---

### Post by devnulljp on 2006-02-15
Using Konsole in KDE, every time I open a new terminal tab session I get the developer credits and GPL reminder.
Not the end of the world, but it’s annoying after the 50th time.
Any idea how to turn it off?

Konsole -> Session -> New Screen Session

The message is:

```
 
Screen version 4.00.02 (FAU) 5-Dec-03

Copyright (c) 1993-2002 Juergen Weigert, Michael Schroeder
Copyright (c) 1987 Oliver Laumann

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied
warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program (see the file COPYING); if not,
write to the Free Software Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.

Send bugreports, fixes, enhancements, t-shirts, money, beer & pizza to screen@uni-erlangen.de 
```

---

### Post by kabus on 2006-02-15
I don't know about Konsole, but to turn off that message in screen you just add

```
startup_message off
```

to your ~/.screenrc.

---

