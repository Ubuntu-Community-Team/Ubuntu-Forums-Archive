---
title: "setting up opengl--linking error"
date: 2009-04-12
forum: General Help
---

### Post by karatekid on 2009-04-12
i want to use functions of the opengl library. So i installed freeglut using synaptic.
However when i write a program which uses the opengl library funtions it does compile perfectly but shows linking error
here's  the output of gcc

```
nitesh@nitesh-desktop:/media/data/Nitesh/Programming/opengl$ gcc -o hello.out hello.c
/tmp/ccAAJVPo.o: In function `init':
hello.c:(.text+0x2a): undefined reference to `glClearColor'
/tmp/ccAAJVPo.o: In function `display':
hello.c:(.text+0x3e): undefined reference to `glClear'
hello.c:(.text+0x5d): undefined reference to `glColor3f'
hello.c:(.text+0x69): undefined reference to `glBegin'
hello.c:(.text+0x85): undefined reference to `glVertex3i'
hello.c:(.text+0xa1): undefined reference to `glVertex3i'
hello.c:(.text+0xbd): undefined reference to `glVertex3i'
hello.c:(.text+0xd9): undefined reference to `glVertex3i'
hello.c:(.text+0xde): undefined reference to `glEnd'
hello.c:(.text+0xe3): undefined reference to `glFlush'
/tmp/ccAAJVPo.o: In function `main':
hello.c:(.text+0x105): undefined reference to `glutInit'
hello.c:(.text+0x111): undefined reference to `glutInitDisplayMode'
hello.c:(.text+0x125): undefined reference to `glutInitWindowPosition'
hello.c:(.text+0x139): undefined reference to `glutInitWindowSize'
hello.c:(.text+0x145): undefined reference to `glutCreateWindow'
hello.c:(.text+0x156): undefined reference to `glutDisplayFunc'
hello.c:(.text+0x15b): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status

```

what do i do?

---

### Post by soltanis on 2009-04-12
You link to the gl library.

```

gcc <options> -lGL -lGLU <files>

```

---

### Post by karatekid on 2009-04-12
thanx for the quick reply....................it working now
can i configure it so that i dont have to link everytime

---

