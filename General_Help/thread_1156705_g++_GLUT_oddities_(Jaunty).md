---
title: "g++ GLUT oddities (Jaunty)"
date: 2009-05-12
forum: General Help
---

### Post by ferrettsyl on 2009-05-12
Google has been unable to address my problem; maybe I'm just searching the wrong things. If anyone else finds a link, please point me to it. Sorry if I posted this in the wrong place.

I'm having odd problems with GLUT; coding in c++, compiling with gcc. I'm running Ubuntu 9.04 on a Dell Inspiron 1520 Laptop, 3.0 GB RAM, 180 GB hdd, NVIDIA graphics card.

Everything compiles okay, but it doesn't execute quite right. It shows the window in the task bar, but it doesn't render the actual window. The window is *there*, I can't click on the icons behind it, and I can even drag and resize it if I click in the right place. But it's quite invisible.
Unless I use the tab-ring in compiz to see thumbs of all my applications; it renders it's thumbnail fine. So where is the problem?

Pics (w/ my name edited out):
[http://www.abpotato.com/images/random/teapot_thumb.png](http://www.abpotato.com/images/random/teapot_thumb.png)
[http://www.abpotato.com/images/random/teapot_drag.png](http://www.abpotato.com/images/random/teapot_drag.png)

I am running this code which I found on a tutorial:
```
#include <iostream>
#include <cstdlib>
#include <GL/glut.h>
using namespace std;

// function prototypes
void disp(void);
void keyb(unsigned char key, int x, int y);


// window identifier
static int win;

int main(int argc, char **argv){
 
  //////////
  // INIT //
  //////////

  // initialize glut
  glutInit(&argc, argv);

  // specify the display mode to be RGB and single buffering 
  // we use single buffering since this will be non animated
  glutInitDisplayMode(GLUT_RGBA | GLUT_SINGLE);

  // define the size
  glutInitWindowSize(500,500);

  // the position where the window will appear
  glutInitWindowPosition(100,100);
  

  // if we would want fullscreen:
  // glutFullScreen();

  // create the window, set the title and keep the 
  // window identifier.
  win = glutCreateWindow("Yet another teapot");

  //////////////
  // CALLBACK //
  //////////////

  glutDisplayFunc(disp);
  glutKeyboardFunc(keyb);
  
  ////////////
  // OPENGL //
  ////////////

  // define the color we use to clearscreen 
  glClearColor(0.0,0.0,0.0,0.0);



  // enter the main loop
  glutMainLoop();
  return 0;
}


void disp(void){

  // do  a clearscreen
  glClear(GL_COLOR_BUFFER_BIT);
  
  // draw something

  glutWireTeapot(0.5);
  // glutSolidTeapot(0.5);
  // glutWireSphere(0.5,100,100);
  // glutSolidSphere(0.5,100,100);
  // glutWireTorus(0.3,0.5,100,100);
  // glutSolidTorus(0.3,0.5,100,100);
  // glutWireIcosahedron();
  // glutSolidIcosahedron();
  // glutWireDodecahedron();
  // glutSolidDodecahedron();
  // glutWireCone(0.5,0.5,100,100);
  // glutSolidCone(0.5,0.5,100,100);
  // glutWireCube(0.5);
  // glutSolidCube(0.5);
}

void keyb(unsigned char key, int x, int y){
  cout << "Pressed key " << key << " on coordinates (" << x << "," << y << ")";
  cout << endl;
  if(key == 'q'){
    cout << "Got q,so quitting " << endl;

    glutDestroyWindow(win);
    exit(0);
  }
}

```

---

### Post by geirha on 2009-05-12
There's a plugin to compiz that can make windows transparent. Don't remember what it's called, but the default keybinding to use it is to hold down ALT and roll the mouse-wheel. Are you able to make it opaque with that? Also, does it show properly if you don't run compiz?
```

metacity --replace &   # Disables compiz temporarily
./your_prog
compiz --replace &     # Enables compiz again

```

Oh and you'd probably gotten a quicker response in the Programming Talk forum under Development and Programming.

---

### Post by ferrettsyl on 2009-05-12
I'll post in the programming section for future problems; I must be blind that I didn't see it.

Yes, it apparently does work if I use metacity instead. I didn't see any window transparency plugins enabled in the compiz manager; alt+mousewheel. Can anyone help me make this work with compiz? I don't want to have any potential users of future programs I make have to switch to metacity just to use it.

---

### Post by geirha on 2009-05-12
Not sure what it could be caused by really. Try creating a new user, log in as that user, enable compiz by choosing Extra in System -> Preferences -> Apperance -> [Visual Effects]. Does it work with a "standard" compiz config?

---

### Post by ferrettsyl on 2009-05-12
I decided to use SDL instead, which seems to be working fine. Thanks anyways for the help though.

---

### Post by SuperElectric on 2010-12-13
I know the original poster has moved on from using GLUT, but here's an answer for others having the same problem. I had the same issue running GLUT (freeglut implementation) on Ubuntu 10.04. Oddly enough, the problem goes away (i.e. the window appears) if you call glutSwapBuffers in your glutDisplayFunc (yes, even when you're not using double buffering).

---

### Post by Ramy89 on 2013-01-27
I have the same problem and the only way to correct it is to disable graphic effects (or replace compiz with metacity). If I call glutSwapBuffers() I get this problem anyway.

---

### Post by oldos2er on 2013-01-28
Old thread closed.

---

