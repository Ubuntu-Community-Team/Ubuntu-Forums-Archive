---
title: "Update matplotlib using pip error"
date: 2014-10-10
forum: Education &amp; Science
---

### Post by proctortc on 2014-10-10
I'm trying to update matplotlib to version 1.4.0, which is not yet availible in the official ubuntu repositories, so I figured I'd turn to pip.
pip install matplotlib --upgrade returned:
    ============================================================================
    Edit setup.cfg to change the build options
    
    BUILDING MATPLOTLIB
                matplotlib: yes [1.4.0]
                    python: yes [2.7.6 (default, Mar 22 2014, 22:59:56)  [GCC
                            4.8.2]]
                  platform: yes [linux2]
    
    REQUIRED DEPENDENCIES AND EXTENSIONS
                     numpy: yes [version 1.8.2]
                       six: yes [using six version 1.5.2]
                  dateutil: yes [using dateutil version 1.5]
                   tornado: yes [using tornado version 3.1.1]
                 pyparsing: yes [using pyparsing version 2.0.1]
                     pycxx: yes [Couldn't import.  Using local copy.]
                    libagg: yes [pkg-config information for 'libagg' could not
                            be found. Using local copy.]
    Traceback (most recent call last):
      File "<string>", line 17, in <module>
      File "/tmp/pip_build_root/matplotlib/setup.py", line 154, in <module>
        result = package.check()
      File "setupext.py", line 940, in check
        if 'No such file or directory\ngrep:' in version:
    TypeError: argument of type 'NoneType' is not iterable
    Complete output from command python setup.py egg_info:
    ============================================================================

pycxx and libagg are not availible on pip (both are c++ libraries, so that makes sense).  I figured I'd just install using ubuntu repos; both are availible.  However, I got this error:




BUILDING MATPLOTLIB

            matplotlib: yes [1.4.0]

                python: yes [2.7.6 (default, Mar 22 2014, 22:59:56)  [GCC

                        4.8.2]]

              platform: yes [linux2]



REQUIRED DEPENDENCIES AND EXTENSIONS

                 numpy: yes [version 1.8.2]

                   six: yes [using six version 1.5.2]

              dateutil: yes [using dateutil version 1.5]

               tornado: yes [using tornado version 3.1.1]

             pyparsing: yes [using pyparsing version 2.0.1]

                 pycxx: yes [version 6.2.5]

                libagg: yes [Requires patches that have not been merged

                        upstream. Using local copy.]

Traceback (most recent call last):

  File "<string>", line 17, in <module>

  File "/tmp/pip_build_root/matplotlib/setup.py", line 154, in <module>

    result = package.check()

  File "setupext.py", line 940, in check

    if 'No such file or directory\ngrep:' in version:

TypeError: argument of type 'NoneType' is not iterable

----------------------------------------
Cleaning up...
Command python setup.py egg_info failed with error code 1 in /tmp/pip_build_root/matplotlib
Storing debug log for failure in ~/.pip/pip.log

It seems it still couldn't find a file.  The  libagg entry says "Requires patches that have not been merged upstream. Using local copy."  I took a look at the libagg website, and it looks like libagg hasn't been maintained since 2007, so I have a hard time imagining that there are actually recent patches.  

Can anyone help out?  Do I have any other options for installing matplotlib?

Thanks!

---

### Post by proctortc on 2014-10-29
I fixed this a while ago, but I think my problem was solved by doing what was suggested in this stackexchange post: [http://stackoverflow.com/questions/25674612/ubuntu-14-04-pip-cannot-upgrade-matplotllib](http://stackoverflow.com/questions/25674612/ubuntu-14-04-pip-cannot-upgrade-matplotllib)

---

