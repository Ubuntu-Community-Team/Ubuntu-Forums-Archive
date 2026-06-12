---
title: "Python pyautogui"
date: 2017-11-07
forum: Education &amp; Science
---

### Post by lijingeorge on 2017-11-07
I was trying to install pyautogui in python 3.6.3. Currently my OS is ubuntu 17.10. This is the difficulty i am facing. Can anybody help me
File "/usr/local/lib/python3.6/site-packages/Xlib/xauth.py", line 43, in __init__
        raw = open(filename, 'rb').read()
    FileNotFoundError: [Errno 2] No such file or directory: '/root/.Xauthority'
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/tmp/pip-build-xxtb56qs/pyautogui/setup.py", line 6, in <module>
        version=__import__('pyautogui').__version__,
      File "/tmp/pip-build-xxtb56qs/pyautogui/pyautogui/__init__.py", line 115, in <module>
        from . import _pyautogui_x11 as platformModule
      File "/tmp/pip-build-xxtb56qs/pyautogui/pyautogui/_pyautogui_x11.py", line 160, in <module>
        _display = Display(os.environ['DISPLAY'])
      File "/usr/local/lib/python3.6/site-packages/Xlib/display.py", line 80, in __init__
        self.display = _BaseDisplay(display)
      File "/usr/local/lib/python3.6/site-packages/Xlib/display.py", line 62, in __init__
        display.Display.__init__(*(self, ) + args, **keys)
      File "/usr/local/lib/python3.6/site-packages/Xlib/protocol/display.py", line 61, in __init__
        name, host, displayno)
      File "/usr/local/lib/python3.6/site-packages/Xlib/support/connect.py", line 91, in get_auth
        return mod.get_auth(sock, dname, host, dno)
      File "/usr/local/lib/python3.6/site-packages/Xlib/support/unix_connect.py", line 103, in new_get_auth
        au = xauth.Xauthority()
      File "/usr/local/lib/python3.6/site-packages/Xlib/xauth.py", line 45, in __init__
        raise error.XauthError('~/.Xauthority: %s' % err)
    Xlib.error.XauthError: ~/.Xauthority: [Errno 2] No such file or directory: '/root/.Xauthority'
    
    ----------------------------------------
Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-build-xxtb56qs/pyautogui/


Kindly help me with this

---

### Post by lijingeorge on 2017-11-17
Solved
I have to do the following to solve it

[B]xhost +
touch ~/.Xauthority
pip install pyautogui
[/B]
Then installation was successful

---

### Post by wildmanne39 on 2017-11-17
You can mark the thread solved by using thread tools at the top of the page.

---

