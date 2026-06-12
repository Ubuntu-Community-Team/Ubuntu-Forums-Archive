---
title: "can't start debugging with monodevelop 2.0"
date: 2009-06-11
forum: General Help
---

### Post by voidman on 2009-06-11
I've just installed monodevelop 2.0 with monodebugger plugin.
"Run Debug" is grayed despite application is compiled in debug mode.
mdb runs fine when started from console.
Also I tried to install monodevelop from the source and got the same result. 
Is it bug or I'm missing something?

---

### Post by voidman on 2009-06-11
I also tried to compile monodevelop from svn and got the following error:
```
Unhandled Exception: Mono.CSharp.InternalErrorException: ./MonoDevelop.Projects.Policies/PolicyBag.cs(101,36): MonoDevelop.Projects.Policies.PolicyBag.IPolicyContainer.DirectGet<T>() ---> System.IndexOutOfRangeException: Array index is out of range.                                                                                                                     
  at Mono.CSharp.TypeParameter+InflatedConstraints.inflate (System.Type t) [0x00000]                                      
  at Mono.CSharp.TypeParameter+InflatedConstraints.inflate (System.Type t) [0x00000]                                      
  at Mono.CSharp.TypeParameter+InflatedConstraints..ctor (Mono.CSharp.GenericConstraints gc, System.Type[] dargs) [0x00000]                                                                                                                         
  at Mono.CSharp.TypeParameter+InflatedConstraints..ctor (Mono.CSharp.GenericConstraints gc, System.Type declaring) [0x00000]                                                                                                                       
  at Mono.CSharp.TypeParameter.DefineType (IResolveContext ec, System.Reflection.Emit.MethodBuilder builder, System.Reflection.MethodInfo implementing, Boolean is_override) [0x00000]                                                              
  at Mono.CSharp.GenericMethod.DefineType (Mono.CSharp.EmitContext ec, System.Reflection.Emit.MethodBuilder mb, System.Reflection.MethodInfo implementing, Boolean is_override) [0x00000]                                                           
  at Mono.CSharp.MethodData.Define (Mono.CSharp.DeclSpace parent, System.String method_full_name) [0x00000]               
  at Mono.CSharp.MethodOrOperator.Define () [0x00000]                                                                     
  at Mono.CSharp.Method.Define () [0x00000]                                                                               
  at Mono.CSharp.TypeContainer+MemberCoreArrayList.DefineContainerMembers () [0x00000]                                    
  --- End of inner exception stack trace ---
  at Mono.CSharp.TypeContainer+MemberCoreArrayList.DefineContainerMembers () [0x00000]
  at Mono.CSharp.TypeContainer.DefineContainerMembers (Mono.CSharp.MemberCoreArrayList mcal) [0x00000]
  at Mono.CSharp.Class.DefineContainerMembers (Mono.CSharp.MemberCoreArrayList list) [0x00000]
  at Mono.CSharp.TypeContainer.DoDefineMembers () [0x00000]
  at Mono.CSharp.Class.DoDefineMembers () [0x00000]
  at Mono.CSharp.TypeContainer.DefineMembers () [0x00000]
  at Mono.CSharp.RootContext.PopulateTypes () [0x00000]
  at Mono.CSharp.Driver.Compile () [0x00000]
  at Mono.CSharp.Driver.Main (System.String[] args) [0x00000]
```
version of mono:
```

mono -V
Mono JIT compiler version 2.0.1 (tarball)
Copyright (C) 2002-2008 Novell, Inc and Contributors. www.mono-project.com
        TLS:           __thread
        GC:            Included Boehm (with typed GC)
        SIGSEGV:       altstack
        Notifications: epoll
        Architecture:  x86
        Disabled:      none

```

Do I need svn version of mono too?
Will manual upgrade hurt my sistem?

---

### Post by directhex on 2009-06-11
There's a race condition bug on Jaunty's kernel which can prevent MDB debugging from working. Installing the 2.4 debugger will fix the issue.

---

### Post by masterofnone on 2009-09-17
> **directhex said:**
> There's a race condition bug on Jaunty's kernel which can prevent MDB debugging from working. Installing the 2.4 debugger will fix the issue.

I am having the same problem:  debugger isn't working with mono-develop.

Could you tell me how to install the 2.4 debugger under Jaunty?  It isn't listed as an option under synaptic package manager.

Sorry, as the username suggests, I am a master of nothing and dabble in a bit of everything.

Jim

---

### Post by masterofnone on 2009-09-17
It seems to be working now.  I think it may have been because of this error:
WARNING: Cannot find Mozilla directory containing **libgtkembedmoz.so**. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

The solution was two steps:
1) Install libxul-dev to provide the libgtkembedmoz.so file
2) edit your home .bashrc file (~/.bashrc) and add the following to the end:
MOZILLA_FIVE_HOME=/usr/lib
export MOZILLA_FIVE_HOME

---

### Post by directhex on 2009-09-18
> **masterofnone said:**
> It seems to be working now.  I think it may have been because of this error:
WARNING: Cannot find Mozilla directory containing **libgtkembedmoz.so**. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

The solution was two steps:
1) Install libxul-dev to provide the libgtkembedmoz.so file
2) edit your home .bashrc file (~/.bashrc) and add the following to the end:
MOZILLA_FIVE_HOME=/usr/lib
export MOZILLA_FIVE_HOME

It has nothing to do with it. It's an unrelated legacy error from when MD used Gecko for the welcome screen

---

### Post by directhex on 2009-09-18
> **masterofnone said:**
> I am having the same problem:  debugger isn't working with mono-develop.

Could you tell me how to install the 2.4 debugger under Jaunty?  It isn't listed as an option under synaptic package manager.

Sorry, as the username suggests, I am a master of nothing and dabble in a bit of everything.

Jim

It's in my PPA.

---

