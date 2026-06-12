---
title: "Installing NumPy for Python 3, when Python 3 is installed in home directory"
date: 2012-08-31
forum: Education &amp; Science
---

### Post by lethalfang on 2012-08-31
Yeah, that's my question. 

I installed Python 3 (from source) into my home directory, and I want to install NumPy and SciPy on it. 
How do I go about it?

I've no idea where to ask this question. If you guys know the right forum, I'll go there. 

Thanks.

---

### Post by ssam on 2012-10-09
there are 2 things you need to get right. running the setup script with the correct version of python, and installing numpy into the right place.

if you do
```

python setup.py install

```
then it will probably use your built in python (/usr/bin/python). but if you do
```

/home/USRNAME/software/bin/python3 setup.py install

```
(or however you call you python3 install), then it willl use that one.

you will probably also want to set a prefix.
```

/home/USRNAME/software/bin/python3 setup.py install --prefix=/home/USRNAME/software/

```
if thats the same as the prefix you used when installing python, then you should be able to import numpy from your python3 now.

otherwsie you may need to set the PYTHONPATH environment variable.

---

