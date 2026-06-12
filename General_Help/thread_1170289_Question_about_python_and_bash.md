---
title: "Question about python and bash"
date: 2009-05-26
forum: General Help
---

### Post by Pitboss on 2009-05-26
Hi. I'm writing a primitive game for bash in python, and I wonder how I can clear the console interactively like watch or top do. The only thing that I worked for now is:

```
    
def clear_screen(self):
      os.system(['clear', 'cl'][os.name == 'nt'])

```

but it just clears the bash, and if I scroll up I can see all the game history. 

Thanks in advance,
Pitboss

---

