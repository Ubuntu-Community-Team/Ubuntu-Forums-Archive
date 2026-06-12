---
title: "Pygame: Trying to use mouse input to check if it is in an image area"
date: 2012-03-31
forum: Gaming &amp; Leisure
---

### Post by demonkingj on 2012-03-31
I have area_roll = Roll.get_rect() which returns the area of the image.

In my event loop I have my quit on certain keys etc.

I have event.type == pygame.MOUSEBUTONDOWN mouseX,mouseY = event.pos #returns position of current place where mouse has been pressed down

I try using : if area_roll.collidepoint(mouseX,mouseY): something

but it never seems to work. collidepoint document says checks point in () with the surface of, in this case, "area_roll"

I am not sure what else to do. I tried using "area_roll.get_size", but doesn't work with collidepoint.

So, in a simple case. If mouse button is down and the mouse position is within the area of the image then execute a command

---

### Post by GWBouge on 2012-04-02
Just a guess here, it's been a while since I've messed with pygame ...

Is it giving you an error, or just not working as expected?  It might be that you're passing the coords as two values, instead of a tuple.

Instead of:
```
if area_roll.collidepoint(mouseX, mouseY):
```

try:
```
if area_roll.collidepoint((mouseX, mouseY)):
```

Or, use the value itself instead of x, y:
```

if event.type == pygame.MOUSEBUTONDOWN:
	if area_roll.collidepoint(event.pos):
```

---

