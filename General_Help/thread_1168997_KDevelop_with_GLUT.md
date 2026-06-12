---
title: "KDevelop with GLUT"
date: 2009-05-24
forum: General Help
---

### Post by Poincare101 on 2009-05-24
I'm trying to get GLUT working with KDevelop. Here's my CMake file:

```

PROJECT(gluttesting)

#if you don't want the full compiler output, remove the following line
#SET(CMAKE_VERBOSE_MAKEFILE ON)

#add definitions, compiler switches, etc.
ADD_DEFINITIONS(-Wall -O2 -g -lglut -lGLU -lGL )

#list all source files here
ADD_EXECUTABLE(gluttesting main.c)

#need to link to some other libraries ? just add them here


 

```

and here is my code: 
```
#include <GL/glut.h> 

void main(int argc, char **argv) {
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_DEPTH | GLUT_SINGLE | GLUT_RGBA);
	glutInitWindowPosition(100,100);
	glutInitWindowSize(320,320);
	glutCreateWindow("3D Tech- GLUT Tutorial");
}

```

When I compile, it doesn't recognize the methods. I triple checked that I have GLUT installed. What should I do about that?
It works fine through emacs and the command line though. I have absoulutely no idea what is wrong.

---

