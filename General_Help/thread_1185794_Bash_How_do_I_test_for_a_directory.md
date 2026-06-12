---
title: "Bash: How do I test for a directory?"
date: 2009-06-12
forum: General Help
---

### Post by Sjeti on 2009-06-12
So I'm writing a quick install script for cmake builds, and I was having a problem with one thing: How do I test to see if a directory already exists?

Here is what I tried:
```

#!/bin/bash
builddir=$(pwd)
cd $builddir
if [ -e CMakeLists.txt ] 
then
  if [ -d $buildir/build ] #Issue is here.
  then
    rm -rf $builddir/build
    echo "Removing old build directory."
  else
    echo "Creating build directory."
  fi
  mkdir $builddir/build
  cd $builddir/build
  cmake ../
  make -j 3
else
  echo "No CMakeLists.txt, aborting build."
fi
exit 0

```

However, this will always return a "Creating new build directory." followed by a quick error stating I can't create a directory that exists.

Any help on my if statement?

---

### Post by jenkinbr on 2009-06-12
> **Sjeti said:**
> So I'm writing a quick install script for cmake builds, and I was having a problem with one thing: How do I test to see if a directory already exists?

Here is what I tried:
```

#!/bin/bash
builddir=$(pwd)
cd $builddir
if [ -e CMakeLists.txt ] 
then
  if [ -d $buildir/build ] #Issue is here.
  then
    rm -rf $builddir/build
    echo "Removing old build directory."
  else
    echo "Creating build directory."
  fi
  mkdir $builddir/build
  cd $builddir/build
  cmake ../
  make -j 3
else
  echo "No CMakeLists.txt, aborting build."
fi
exit 0

```

However, this will always return a "Creating new build directory." followed by a quick error stating I can't create a directory that exists.

Any help on my if statement?

Try changing your line to read 
```
if [ -d "$builddir/build" ] #Issue is here.
```

---

### Post by gradinaruvasile on 2009-06-12
[ -d $build[COLOR="Red"]d[/COLOR]ir/build ]
?

---

### Post by Sjeti on 2009-06-12
Oh f#&* that.

Both corrections fixed it.  Thanks guys. :D

---

### Post by jenkinbr on 2009-06-12
:)  No problem.

---

