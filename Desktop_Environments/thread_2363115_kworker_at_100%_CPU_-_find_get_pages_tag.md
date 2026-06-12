---
title: "kworker at 100% CPU - find_get_pages_tag"
date: 2017-06-06
forum: Desktop Environments
---

### Post by thevsdr on 2017-06-06
Hey guys,

I have just installed ubuntu-mate on 17.04 on my Dell Precision 5510, it has 16GB of ram, i7-6820HQ [running intel-microcode] and a Quadro M1000M [ running nvidia-375]. Kernel version is: 4.10.0-21-generic.

I initially installed this without a swap as 16gb of ram "should" be ok for what i needed however apps started to crash due to "out of memory", i checked "free -m" showed it was all cached but still ~10gb available.. 
This is odd, but figured i underestimated the need for swap in this case so i added a 32GB swap partition and now i have kworker/u16:4 running at 100% with the the below trace:

```
Samples: 156K of event 'cycles', Event count (approx.): 105130510564Overhead  Command        Shared Object      Symbol                                                                  &#9670;
  50.43%  kworker/u16:4  [kernel.kallsyms]  [k] find_get_pages_tag                                                  &#9618;
  19.30%  kworker/u16:4  [kernel.kallsyms]  [k] write_cache_pages                                                   &#9618;
  12.32%  kworker/u16:4  [kernel.kallsyms]  [k] release_pages                                                       &#9618;
  10.32%  kworker/u16:4  [kernel.kallsyms]  [k] unlock_page                                                         &#9618;
   5.87%  kworker/u16:4  [kernel.kallsyms]  [k] radix_tree_next_chunk                                               &#9618;
   0.65%  kworker/u16:4  [kernel.kallsyms]  [k] _cond_resched                                                       &#9618;
   0.35%  kworker/u16:4  [kernel.kallsyms]  [k] lru_add_drain_cpu                                                   &#9618;
   0.23%  kworker/u16:4  [kernel.kallsyms]  [k] pagevec_lookup_tag                                                  &#9618;
   0.14%  kworker/u16:4  [kernel.kallsyms]  [k] __pagevec_release                                                   &#9618;
   0.08%  kworker/u16:4  [kernel.kallsyms]  [k] mem_cgroup_uncharge_list                                            &#9618;
   0.07%  kworker/u16:4  [kernel.kallsyms]  [k] free_hot_cold_page_list                                             &#9618;
   0.02%  kworker/u16:4  [kernel.kallsyms]  [k] _aesni_enc1                                                         &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] vma_interval_tree_subtree_search                                    &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] update_blocked_averages                                             &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] smp_call_function_many                                              &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] rcu_check_callbacks                                                 &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] intel_pstate_update_util                                            &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] perf_event_task_tick                                                &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] _raw_spin_lock                                                      &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] update_wall_time                                                    &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] native_queued_spin_lock_slowpath                                    &#9618;
   0.01%  kworker/u16:4  [kernel.kallsyms]  [k] cpuacct_charge                                                      &#9618;
   0.00%  kworker/u16:4  [kernel.kallsyms]  [k] update_load_avg                                                     &#9618;
   0.00%  kworker/u16:4  [kernel.kallsyms]  [k] irq_exit                                     
```

This looks to me that the OS is having problems with the swap and paging in and out however free shows there is only 937mb in swap and plenty of "Available" memory
```
$ free -m              total        used        free      shared  buff/cache   available
Mem:          15860        2495         150         170       13214       12851
Swap:         31999         937       31062



```

The only other thing of note, i am also running a windows VM in VMware Workstation which is the biggest ram hog set at 4096 MB and 1 CPU, 2 Cores. Intel VT-x/EPT. This should not be causing this and the vmware-vmx process is not showing anything abnormal.
```
  PID    TID RUID     EUID       THR SYSCPU USRCPU  VGROW   RGROW  RDDSK  WRDSK ST  EXC S CPUNR  CPU  CMD        1/2  
6304      - root     root         1  9.99s  0.00s     0K      0K     0K  7584K --    - R     2 100%  kworker/u16:4
  4286      - wardd    wardd       23  6.14s  0.06s     0K  -20.3M    32K  9204K --    - S     0  62%  vmware-vmx
  9391      - wardd    wardd       16  0.10s  0.93s     0K    572K     0K     0K --    - S     5  10%  chrome
  2638      - wardd    wardd        5  0.08s  0.49s  1280K   1148K     0K     0K --    - S     0   6%  chrome



```


Anyone know what i can do to either force the kernel to release this ram or some how restrict how much it is caching?

Thank you

---

