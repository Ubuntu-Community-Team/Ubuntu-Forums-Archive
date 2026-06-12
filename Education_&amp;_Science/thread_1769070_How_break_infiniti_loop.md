---
title: "How break infiniti loop"
date: 2011-05-27
forum: Education &amp; Science
---

### Post by new7linux on 2011-05-27
Hi guy am very tired because this question:-

how can break or exit from  infinity or endless loop,,

let we have process A  ,write by c++ language, process A contain this LOOP

int x=1;
while(x<10)
{
x++;
x=1;
}

as you see the condition will be true for ever"because x=1"

i know that in single task operating system"16 bit", the CPU will enter this loop and not exit from this loop,we can break this loop by only reset the computer,

but in multitasking operating system"32 bit",,the CPU must exit from this loop to execute another process,,

then my question how can exit from this loop"in 32 bit or multitasking operating system"

---

### Post by NovaAesa on 2011-05-28
If I understand your question correctly, it's the Process Scheduler inside the multitasking operating system's kernel that switches between processes. When a process switch occurs (switching from process A to the next process in the ready-queue), the loop will be halted.

---

### Post by new7linux on 2011-05-28
> **NovaAesa said:**
> If I understand your question correctly, it's the Process Scheduler inside the multitasking operating system's kernel that switches between processes. When a process switch occurs (switching from process A to the next process in the ready-queue), the loop will be halted.

yes, you understand my question,

you say that Process Scheduler will make switch between the processes"I understand that"

but:-
I know that when a process executing by the CPU, this process Will become controlling the PC,

so how the controlling return to "Process Scheduler" again???

thank you>>

---

### Post by NovaAesa on 2011-05-28
Control returns to the process scheduler on an event known as an "interrupt". [http://en.wikipedia.org/wiki/Interrupt](http://en.wikipedia.org/wiki/Interrupt) Basically, every xzy ticks of the CPU an interrupt will be triggered that tells the currently running process to save its state and pass control over to the process scheduler. The process scheduler then can either decide to let the original process have control again, or let another process have its turn on the CPU.

---

### Post by new7linux on 2011-05-28
> **NovaAesa said:**
> Control returns to the process scheduler on an event known as an "interrupt". [http://en.wikipedia.org/wiki/Interrupt](http://en.wikipedia.org/wiki/Interrupt) Basically, every xzy ticks of the CPU an interrupt will be triggered that tells the currently running process to save its state and pass control over to the process scheduler. The process scheduler then can either decide to let the original process have control again, or let another process have its turn on the CPU.

ok thank you, now i understand,

Sorry for prolonging but i have last question:-

this interrupt is occur by an event"like a process request an I/O device" or 
by  a timer   "generate interrupt every  specific time "???

---

### Post by NovaAesa on 2011-06-01
> **new7linux said:**
> ok thank you, now i understand,

Sorry for prolonging but i have last question:-

this interrupt is occur by an event"like a process request an I/O device" or 
by  a timer   "generate interrupt every  specific time "???

That will depend entirely on the scheduling algorithm. Usually the interrupts occur on the basis of a fixed timer. Depending on the algorithm though, a new process entering the ready queue with a high priority can cause the current process to be kicked off the CPU.

---

### Post by new7linux on 2011-06-01
> **NovaAesa said:**
> That will depend entirely on the scheduling algorithm. Usually the interrupts occur on the basis of a fixed timer. Depending on the algorithm though, a new process entering the ready queue with a high priority can cause the current process to be kicked off the CPU.

OK

Thank you very much.

---

