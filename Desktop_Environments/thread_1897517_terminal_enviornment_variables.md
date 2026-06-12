---
title: "terminal enviornment variables"
date: 2011-12-19
forum: Desktop Environments
---

### Post by cpgos on 2011-12-19
Could somebody please explain how to get the following command to run when I open a terminal window in Ubuntu 11.10:

source /opt/intel/bin/compilervars.sh ia32

This command is needed to set the environment variables for an Intel Fortran compiler that I want to use.


Best regards,
cpgos

---

### Post by Lars Noodén on 2011-12-19
It should run just as you have written it.  Does [font=Courier New]/opt/intel/bin/compilervars.sh[/font] exist?  What's the output of this:

```

ll /opt/intel/bin/compilervars.sh

```

---

### Post by cpgos on 2011-12-19
Lars Nooden,
Thank you for your response.

/opt/intel/bin/compilervars.sh exists in the folder where the Intel compiler is installed. When I enter and run this command manually no errors or messages are generated but the compiler operates as required.

I would like to avoid having to do this each time and instead have the command implemented automatically when I open a terminal.

There seems to be some way do do this via the edit\preferences menu but it is not clear to me how to do so.

Best regards,
cpgos

---

### Post by Lars Noodén on 2011-12-20
You could try putting it in [font=Courier New].bashrc[/font] so that it will run every time you open the terminal.

---

### Post by cpgos on 2011-12-22
Lars Nooden,
I have done as you suggested and the terminal now responds as required.

Best regards,
cpgos

---

