---
title: "Pygame Help"
date: 2010-11-22
forum: Gaming &amp; Leisure
---

### Post by ngrieb on 2010-11-22
I am currently building my first pygame in order to better learn python and pass some time, and I have run into a small issue which I was hoping someone out there could help me fix. I had the main menu of the game running such that one could use the mouse buttons and enter to select the components, but I changed the menu to now read the mouse y and move to the corresponding menu option. I am using something like this:

event = pygame.event.wait()
x, y = pygame.mouse.get_pos()
if other_menu_option height < y <= some_menu_option_height:
   highlight_menu_option
if event.type == pygame.MOUSEBUTTONDOWN:
   if pygame.mouse.get_pressed() == (1, 0, 0):
      play_game()

the problem is that now when I click it takes forever for python (2.6) to recognize the click at all. Should I not be using the event.wait() function or is there something else slowing this down all of the sudden? I mean everything else seems to be working very well (including moving sprites etc.). What am I doing wrong?

---

### Post by ngrieb on 2010-11-22
[SOLVED]

Alright I figured it out... it looks like my mistake was calling an event type near the bottom of my code instead of having a large block of events directly after the pygame.event.wait() call. Obviously the calls to images and image manipulations were slowing the event reading down quite a bit. 

Hope this helps someone else in the future maybe...

I am still running into a few snags though:
Is there any way to detect the mouse wheel up and down actions in pygame?
I have looked online and tried various combos of mouse getting options...

I found one way but it uses the command pygame.MOUSEBUTTONDOWN, and after moving code and taking this command out of pygame the in the above things ran smoothly. It seems like this command is extremely slow at getting data. Does anyone else experience this as well? How can I fix it?

---

