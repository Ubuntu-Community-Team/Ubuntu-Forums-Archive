---
title: "Pygame basics"
date: 2009-10-23
forum: Gaming &amp; Leisure
---

### Post by TironN on 2009-10-23
Hey there. I'm running Ubuntu 9.04 and have just installed pygame using synaptics.

after attempting to go through the tutorial on the pygame website:
```

[FONT=monospace] 1    import sys, pygame[/FONT]
 [FONT=monospace] 2    pygame.init()[/FONT]
 [FONT=monospace] 3[/FONT]
 [FONT=monospace] 4    size = width, height = 320, 240[/FONT]
 [FONT=monospace] 5    speed = [2, 2][/FONT]
 [FONT=monospace] 6    black = 0, 0, 0[/FONT]
 [FONT=monospace] 7[/FONT]
 [FONT=monospace] 8    screen = pygame.display.set_mode(size)[/FONT]
 [FONT=monospace] 9[/FONT]
 [FONT=monospace]10    ball = pygame.image.load("ball.bmp")[/FONT]
 [FONT=monospace]11    ballrect = ball.get_rect()[/FONT]
 [FONT=monospace]12[/FONT]
 [FONT=monospace]13    while 1:[/FONT]
 [FONT=monospace]14        for event in pygame.event.get():[/FONT]
 [FONT=monospace]15            if event.type == pygame.QUIT: sys.exit()[/FONT]
 [FONT=monospace]16[/FONT]
 [FONT=monospace]17        ballrect = ballrect.move(speed)[/FONT]
 [FONT=monospace]18        if ballrect.left < 0 or ballrect.right > width:[/FONT]
 [FONT=monospace]19            speed[0] = -speed[0][/FONT]
 [FONT=monospace]20        if ballrect.top < 0 or ballrect.bottom > height:[/FONT]
 [FONT=monospace]21            speed[1] = -speed[1][/FONT]
 [FONT=monospace]22[/FONT]
 [FONT=monospace]23        screen.fill(black)[/FONT]
 [FONT=monospace]24        screen.blit(ball, ballrect)[/FONT]
 [FONT=monospace]25        pygame.display.flip()[/FONT]
```

at line 10 I get an image not found.
Tips?

---

### Post by Ferramentapenna on 2009-12-05
Have you made sure the ball.bmp file is in the same location as the source file?  If it isn't you'll need to point line 10 to it.

---

### Post by Chesnut on 2009-12-05
Same as Ferramentapenna:

Put the ball.bmp file in the same folder as the source file.

Also, make sure your 'ball' image is not JPG or PNG, but BMP. Or just change the value.

---

