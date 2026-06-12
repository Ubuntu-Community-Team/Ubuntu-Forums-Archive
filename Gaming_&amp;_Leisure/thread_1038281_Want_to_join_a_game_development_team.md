---
title: "Want to join a game development team?"
date: 2009-01-12
forum: Gaming &amp; Leisure
---

### Post by iamscuzzo on 2009-01-12
I want to make 2D games aimed at the open source/free software community. I am new to programming, so I got a python book and started reading. I then tried [pygame ]("http://www.pygame.org")and played around with it. 

It would be cool to have a buddy or more, to help plan out things, get help, and have a different perspective on things. If you are interested in joining, PM me and post here. I can share more details when we get in touch. Thanks

Playing around with pygame:
[http://www.youtube.com/watch?v=rzYzrjCqABo](http://www.youtube.com/watch?v=rzYzrjCqABo)

```

# Collision
# Testing collision with pygame
# Haroon Khalid - 12/02/2008

import pygame
import random
from sys import exit

# INITIALIZE PYGAME
pygame.init()

# SET WINDOW CAPTION
pygame.display.set_caption("Collision Test")

# SET WINDOW RESOLUTION
resolution = (286, 80)
screen = pygame.display.set_mode(resolution, 0, 32)

# SET UP THE FONT AND COLOR
default_font = pygame.font.get_default_font()
font = pygame.font.SysFont(default_font, 20)
white = (255,255,255)

class Enemy(object):
    def __init__(self):
        enemy = 'enemy.png'
        enemyimg = pygame.image.load(enemy).convert()
        enemyimg.set_colorkey((76,88,100))
        self.image = enemyimg
        self.rect = self.image.get_rect()
        self.rect.x = 0
        self.rect.y = 0
    
    def update(self):
        if self.rect.x < 100:
            enemies.remove(self)
        else:
            self.rect.x -= 1
            screen.blit(self.image, (self.rect.x,self.rect.y))

class Bullet(object):
    def __init__(self):
        bullet = 'bullet.png'
        bulletimg = pygame.image.load(bullet).convert()
        self.image = bulletimg
        self.rect = self.image.get_rect()
        self.rect.x = 0
        self.rect.y = 0
        
    def update(self):
        if self.rect.x > 300:
            bullets.remove(self)
        else:
            self.rect.x += 10
            screen.blit(bulletimg,(self.rect.x,self.rect.y))

class Player(object):
    def __init__(self):
        self.x = 0
        self.y = 0
        self.alive = True
        player = 'player.png'
        playerimg = pygame.image.load(player).convert()
        self.image = playerimg

def test_input():
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            exit()
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                shot_snd.play()
                create_bullet()
            if event.key == pygame.K_z:
                create_enemy()

def draw_stats():
    white = (255, 255, 255)
    bulletamt = str(len(bullets))
    bullettxt = font.render("Bullets: " + bulletamt, True, white)
    enemyamt = str(len(enemies))
    enemytxt = font.render("Enemies: " + enemyamt, True, white)
    screen.blit(enemytxt, (1, 1))    
    screen.blit(bullettxt, (1, 14))
    
def create_enemy():
    E = Enemy()
    E.rect.x = random.randint(200,250)  
    E.rect.y = 0
    enemies.append(E)
    
def update_enemy():
    for enemy in enemies:
        enemy.update()

def create_bullet():
    b = Bullet()
    b.rect.x = p1.x + 25
    b.rect.y = p1.y + 7
    bullets.append(b)

def update_bullet():
    for bullet in bullets:
        bullet.update()

# CHECK FOR COLLISION BY COMPARING RECTS W/ LISTS
def check_hit():
    for j in bullets:
        for k in enemies:
            if j.rect.colliderect(k.rect):
                zap_snd.play()
                if j in bullets:
                    bullets.remove(j)
                if k in enemies:
                    enemies.remove(k)

# SOUNDS
shot_snd = pygame.mixer.Sound("shot.ogg")
hit_snd = pygame.mixer.Sound("hit.ogg")
zap_snd = pygame.mixer.Sound("zap.ogg")

# LISTS FOR STORING 
bullets = []
enemies = []

# CREATE THE PLAYERS SHIP AND POSITION
p1 = Player()
p1.x = 0
p1.y = 29

# SETTING UP SPRITES
bullet = 'bullet.png'
bulletimg = pygame.image.load(bullet).convert()
bg = 'bg.png'
bgimg = pygame.image.load(bg).convert()

# MAIN GAME LOOP
while True:
    
    screen.blit(bgimg, (0,0))
    draw_stats()
    test_input()
    check_hit()
    screen.blit(p1.image, (p1.x, p1.y))
    update_bullet()
    update_enemy()
    pygame.display.update()
    pygame.time.delay(25)

```

---

### Post by eragon100 on 2009-01-12
> **iamscuzzo said:**
> I want to make 2D games aimed at the open source/free software community. I am new to programming, so I got a python book and started reading. I then tried [pygame ]("http://www.pygame.org")and played around with it. 

It would be cool to have a buddy or more, to help plan out things, get help, and have a different perspective on things. If you are interested in joining, PM me and post here. I can share more details when we get in touch. Thanks

Playing around with pygame:
[http://www.youtube.com/watch?v=rzYzrjCqABo](http://www.youtube.com/watch?v=rzYzrjCqABo)

```

# Collision
# Testing collision with pygame
# Haroon Khalid - 12/02/2008

import pygame
import random
from sys import exit

# INITIALIZE PYGAME
pygame.init()

# SET WINDOW CAPTION
pygame.display.set_caption("Collision Test")

# SET WINDOW RESOLUTION
resolution = (286, 80)
screen = pygame.display.set_mode(resolution, 0, 32)

# SET UP THE FONT AND COLOR
default_font = pygame.font.get_default_font()
font = pygame.font.SysFont(default_font, 20)
white = (255,255,255)

class Enemy(object):
    def __init__(self):
        enemy = 'enemy.png'
        enemyimg = pygame.image.load(enemy).convert()
        enemyimg.set_colorkey((76,88,100))
        self.image = enemyimg
        self.rect = self.image.get_rect()
        self.rect.x = 0
        self.rect.y = 0
    
    def update(self):
        if self.rect.x < 100:
            enemies.remove(self)
        else:
            self.rect.x -= 1
            screen.blit(self.image, (self.rect.x,self.rect.y))

class Bullet(object):
    def __init__(self):
        bullet = 'bullet.png'
        bulletimg = pygame.image.load(bullet).convert()
        self.image = bulletimg
        self.rect = self.image.get_rect()
        self.rect.x = 0
        self.rect.y = 0
        
    def update(self):
        if self.rect.x > 300:
            bullets.remove(self)
        else:
            self.rect.x += 10
            screen.blit(bulletimg,(self.rect.x,self.rect.y))

class Player(object):
    def __init__(self):
        self.x = 0
        self.y = 0
        self.alive = True
        player = 'player.png'
        playerimg = pygame.image.load(player).convert()
        self.image = playerimg

def test_input():
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            exit()
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                shot_snd.play()
                create_bullet()
            if event.key == pygame.K_z:
                create_enemy()

def draw_stats():
    white = (255, 255, 255)
    bulletamt = str(len(bullets))
    bullettxt = font.render("Bullets: " + bulletamt, True, white)
    enemyamt = str(len(enemies))
    enemytxt = font.render("Enemies: " + enemyamt, True, white)
    screen.blit(enemytxt, (1, 1))    
    screen.blit(bullettxt, (1, 14))
    
def create_enemy():
    E = Enemy()
    E.rect.x = random.randint(200,250)  
    E.rect.y = 0
    enemies.append(E)
    
def update_enemy():
    for enemy in enemies:
        enemy.update()

def create_bullet():
    b = Bullet()
    b.rect.x = p1.x + 25
    b.rect.y = p1.y + 7
    bullets.append(b)

def update_bullet():
    for bullet in bullets:
        bullet.update()

# CHECK FOR COLLISION BY COMPARING RECTS W/ LISTS
def check_hit():
    for j in bullets:
        for k in enemies:
            if j.rect.colliderect(k.rect):
                zap_snd.play()
                if j in bullets:
                    bullets.remove(j)
                if k in enemies:
                    enemies.remove(k)

# SOUNDS
shot_snd = pygame.mixer.Sound("shot.ogg")
hit_snd = pygame.mixer.Sound("hit.ogg")
zap_snd = pygame.mixer.Sound("zap.ogg")

# LISTS FOR STORING 
bullets = []
enemies = []

# CREATE THE PLAYERS SHIP AND POSITION
p1 = Player()
p1.x = 0
p1.y = 29

# SETTING UP SPRITES
bullet = 'bullet.png'
bulletimg = pygame.image.load(bullet).convert()
bg = 'bg.png'
bgimg = pygame.image.load(bg).convert()

# MAIN GAME LOOP
while True:
    
    screen.blit(bgimg, (0,0))
    draw_stats()
    test_input()
    check_hit()
    screen.blit(p1.image, (p1.x, p1.y))
    update_bullet()
    update_enemy()
    pygame.display.update()
    pygame.time.delay(25)

```

Hi, I am in the same position as you, also learning pygame. Just getting started, it looks as tough you already have a bit more knowledge in pygame than me. I do know about basic general python stuff tough, lists, tuples, variables, for and while loops, dictionarys, making functions and objects, private/public methods/attributes, inheritance, working with files, exceptions, etc...

Anyway, what do you want to make? Something violent? I would love to create a fighting game :popcorn:

Also, keep in mind you can use OpenGL with python too for 3d stuff, you can even use it with pygame! (tough I have *no idea* how to use opengl) :wink:

I am still very much getting started with pygame, this is the kind of code I can create for it right now:


There was indentation before copy and paste removed it, by the way.
*********** CODE **************

#!/usr/bin/env python

import pygame
from pygame.locals import *
from sys import exit
import os
import random
pygame.init()

base_dir = os.getcwd()      # This is the base directory, from which we move into the other folders as needed
background_image_filename = "data/pictures/background.jpg"

os.chdir(base_dir)          # Switch back to base directory from pictures to load (random) music file

# Create screen, set pygame settings and load background
screen = pygame.display.set_mode((1024, 768), HWSURFACE, 32)
pygame.display.set_caption("Space Pong!")
pygame.mouse.set_visible(0)
background = pygame.image.load(background_image_filename).convert()

# Next three blocks: initial variables (used for drawing objects)
player_paddle_pos = (100, 374)
player_paddle_color = (255, 0, 0)
player_paddle_size = (10, 80)

ai_paddle_pos = (924, 374)
ai_paddle_color = (0, 0, 255)
ai_paddle_size = (10, 80)

ball_color = (0, 255, 0)
ball_pos = ((1024 / 2), (768 / 2))
ball_radius = 15

while True:
    
    # If no music is playing, load and play a random music file.
    while (pygame.mixer.music.get_busy() == False):
        music_choice = random.randrange(4 + 1)
        if (music_choice == 1):
            pygame.mixer.music.load("data/music/background_music_1.ogg")
        elif (music_choice == 2):
            pygame.mixer.music.load("data/music/background_music_2.ogg")
        elif (music_choice == 3):
            pygame.mixer.music.load("data/music/background_music_3.ogg")
        elif (music_choice == 4):
            pygame.mixer.music.load("data/music/background_music_4.ogg")
        pygame.mixer.music.play()
        os.chdir(base_dir)
    
    screen.blit(background, (0, 0))
    
    # Here we dras the two paddles and the ball. This is done at the beginning of
    # the game loop because the rest of the loop is devoted to calculating the new
    # position (and in the case of the ball also direction) of the paddles and ball.
    screen.lock()
    pygame.draw.rect(screen, player_paddle_color, Rect(player_paddle_pos, player_paddle_size))
    pygame.draw.rect(screen, ai_paddle_color, Rect(ai_paddle_pos, ai_paddle_size))
    pygame.draw.circle(screen, ball_color, ball_pos, ball_radius)
    screen.unlock()
    
    # The ai paddle simply follows the player (with a time delay), because we assume the player is smart :)
    if (player_paddle_pos[1] - ai_paddle_pos[1] > 0):   # True if player's paddle is above AI paddle
        ai_paddle_pos = (ai_paddle_pos[0], ai_paddle_pos[1] + 4) # move AI paddle up
    elif (player_paddle_pos[1] - ai_paddle_pos[1] < 0): # True if player's paddle is below AI paddle
        ai_paddle_pos = (ai_paddle_pos[0], ai_paddle_pos[1] - 4) # move AI paddle down
    
    # Here we set two booleans, ball_left and ball_down, which indicate the directions the ball
    # is travelling in. If it hits a wall it should change direction, offcourse.
    if (ball_pos[0] >= 1024):
        ball_left = True
    elif (ball_pos[0] <= 1024):
        ball_left = False
    if (ball_pos[1] >= 768):
        ball_down = True
    elif (ball_pos[0] <= 768):
        ball_down = False
    
    # Based on the booleans set above, we move the ball here.
    if ((ball_down == False) and (ball_left == False)):
        ball_pos = (ball_pos[0] + 3, ball_pos[1] + 3)
    elif ((ball_down == False) and (ball_left == True)):
        ball_pos = (ball_pos[0] - 3, ball_pos[1] + 3)
    elif ((ball_down == True) and (ball_left == False)):
        ball_pos = (ball_pos[0] + 3, ball_pos[1] - 3)
    elif ((ball_down == True) and (ball_left == True)):
        ball_pos = (ball_pos[0] - 3, ball_pos[1] - 3)
       
        
    for event in pygame.event.get():
        if (event.type == MOUSEMOTION):
            unused, player_paddle_y = pygame.mouse.get_pos()
            player_paddle_pos = (100, player_paddle_y)
            
        elif event.type == KEYDOWN:
            if (event.key == K_f):
                pygame.display.toggle_fullscreen()
                
        elif (event.type == QUIT):
            exit()
            
    pygame.display.update()


************ END CODE **************

I have also written a simple text adventure game with music and sound, fighting, classes, saving and loading, etc. No story, tough. :wink:

Can't show it to you here, because the data folder is to big for an attachment :(

Anyway, what do you want to make, I think I am interested !

---

### Post by iamscuzzo on 2009-01-12
eragon, do you have AIM or gmail? Email me [email]i.am.scuzzo@gmail.com[/email] so I have it for reference. We can speak more in private about what we can do. Im so happy that you replied man, you made my day.

---

### Post by hikaricore on 2009-01-12
See I told you people would respond. :p

---

### Post by iamscuzzo on 2009-01-12
> **hikaricore said:**
> See I told you people would respond. :p

thanks dude, you are one cool mudda choka! :popcorn:

---

### Post by eragon100 on 2009-01-14
> **iamscuzzo said:**
> thanks dude, you are one cool mudda choka! :popcorn:

One cool WHAT?? Anyway, I have send you a mail, but have to go to school now, I will be back this afternoon/evening (my time zone) :wink:

---

### Post by Jion_Wansu on 2009-01-14
anyone up for making a 2D game similar to a Street Fighter or Mortal Kombat game?

---

### Post by EdThaSlayer on 2009-01-15
> **Jion_Wansu said:**
> anyone up for making a 2D game similar to a Street Fighter or Mortal Kombat game?

There is already one called OpenMortal.
Pretty funny game though,very unique characters.
You can find it on [http://openmortal.sourceforge.net/](http://openmortal.sourceforge.net/)


I think an epic rpg would be nice. Imagine one with real---voice acting?
If you can find some people to do their voice-acting.

A Dungeons and Dragons clone would be nice, but then again, you could improve a game slowly so it evolves over time into an rpg game with many options.

Pygame does sound interesting, remember trying it a long time back and the tutorials have improved I have to say!

---

### Post by Firestem4 on 2009-01-15
well i have no scripting knowledge whatsoever. However, depending what you are doing (ie: RPG or something) I am a fairly competent writer and I love fantasy and sci-fi. If you need someone like this for story arcs and such. Drop me a line.

Aim: Firestem4
MSN: [email]Firestem4@gmail.com[/email]

If you want to see a sample of some writing i have done i can provide that too. And this goes for anyone who wants to try and develop a game. Not just the thread starter =)

---

### Post by eragon100 on 2009-01-15
> **Jion_Wansu said:**
> anyone up for making a 2D game similar to a Street Fighter or Mortal Kombat game?

We are planning on making a fighting game, yes :wink:

---

### Post by iamscuzzo on 2009-01-16
> **Jion_Wansu said:**
> anyone up for making a 2D game similar to a Street Fighter or Mortal Kombat game?

edit edit

---

### Post by MrWaffless on 2010-03-09
Hey I want to join also.

AIM:thelocoboy4
E-MAIL:ranjelpineda@yahoo.com

---

### Post by The Data Diviner on 2010-03-10
This sounds really cool.  I would love to be involved, but I'm not sure I have the time or experience.  Nevertheless, let me know what you guys decide and when you're starting.  

E-mail: [email]datadjango@gmail.com[/email]

---

