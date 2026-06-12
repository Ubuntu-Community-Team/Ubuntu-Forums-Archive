---
title: "POV-Ray is a neat programme."
date: 2007-10-10
forum: Desktop Environments
---

### Post by tehet on 2007-10-10
I've been playing with POV-Ray today and it's pretty cool! And then I made the mandatory Ubuntu logo.

In case anyone wants to tinker, here's the file:
```
#include "colors.inc"

camera {
  location <0, 0, -5>
  look_at 0
  angle 0
}

background {color rgb <.7 .8 .9> }

light_source { <-900, 300, -1000> White }

#declare Box = box { <0, -1, -2>, <20, 1, 2>
}
#declare RotateCutOut = 120*z;
#declare CutOutPart = union {
  object { Box
    rotate RotateCutOut
  }
  object { cylinder {
    <-16, 0, -2>, <-16, 0, 2>, 4
    }
  }
}

#declare CutOut = union {
  object { CutOutPart
  }
  object { CutOutPart
    rotate RotateCutOut
  }
  object { CutOutPart
    rotate -RotateCutOut
  }
  object { cylinder { <0, 0, -2>, <0, 0, 2>, 10 }
  }
}

#declare Body = object {
  cylinder { <0, 0, -1>, <0, 0, 1>, 16 }
}

#declare ArmsTexture = texture {
  pigment { Silver }
  finish {
    ambient .1
    diffuse .4
    reflection .25
    specular 1
    metallic
  }
}

#declare HeadsTexture = texture {
  pigment { Red }
  finish {
    ambient .2
    diffuse .1
    reflection .9
    specular 1
    metallic
  }
}

#declare Head = object {
  cylinder { <0, 0, 1>, <0, 0, -1>, 3 }
  translate <-16, 0, 0>
  texture { HeadsTexture }
}

#declare Heads = union {
  object { Head }
  object { Head
    rotate <0, 0, 120>
  }
  object { Head
    rotate <0, 0, -120>
  }
}

#declare Arms = difference {
  object { Body }
  object { CutOut }
  texture { ArmsTexture }
}

#declare Logo = union {
  object { Arms }
  object { Heads }
}

object {
  Logo
  scale .1
  rotate <0, 0, 0>
  }
plane {
  <0, 1, 0>, -2
    pigment {
      checker color White, color Green
  }
}
```

Got POV-Ray?

Ps.: Does anyone know what the proper dimensions of the Ubuntu logo are? As in:
inner radius
outer radius
width of the space between the arms
radius of the heads
radius of the ... erm ... 'necks'?

---

### Post by thisllub on 2007-10-10
Nice

---

### Post by Lord Illidan on 2007-10-10
Nice, thanks for the code..

---

