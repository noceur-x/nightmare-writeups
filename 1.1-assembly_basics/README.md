# First Binary

## Disassembled content

```nasm
080483fb <main>:
 80483fb:       8d 4c 24 04             lea    ecx,[esp+0x4]
 80483ff:       83 e4 f0                and    esp,0xfffffff0
 8048402:       ff 71 fc                push   DWORD PTR [ecx-0x4]
 8048405:       55                      push   ebp
 8048406:       89 e5                   mov    ebp,esp
 8048408:       51                      push   ecx
 8048409:       83 ec 04                sub    esp,0x4
 804840c:       83 ec 0c                sub    esp,0xc
 804840f:       68 b0 84 04 08          push   0x80484b0
 8048414:       e8 b7 fe ff ff          call   80482d0 <puts@plt>
 8048419:       83 c4 10                add    esp,0x10
 804841c:       b8 00 00 00 00          mov    eax,0x0
 8048421:       8b 4d fc                mov    ecx,DWORD PTR [ebp-0x4]
 8048424:       c9                      leave  
 8048425:       8d 61 fc                lea    esp,[ecx-0x4]
 8048428:       c3                      ret    
 8048429:       66 90                   xchg   ax,ax
 804842b:       66 90                   xchg   ax,ax
 804842d:       66 90                   xchg   ax,ax
 804842f:       90                      nop
```

## Key Concepts

### Registers (x86_64)

   `ecx` -> extended counter register -> usually used for storing the fourth parameter of a function or as a counter.

   `esp` -> extended stack pointer. -> points to the top of the stack.

   `ebp` -> extended base pointer. -> points to the bottom of the stack frame.

   `eax` -> holds function return values
   
   `ax` -> lower 2 bytes of eax.  

   `eip` -> extended instruction pointer

### Main Instructions Found

    # x86 Assembly Instructions

    * **`lea destination, [calculated_address]`**  
    `lea` calculates an address and stores it inside `destination`.

    * **`and firstNumber, secondNumber`**  
      Applies an `AND` operation between two numbers. It compares the two numbers bit by bit and gives `1` if both bits are `1`, otherwise `0`.

    * **`push x`**  
      `x` is pushed into the stack. If `x` occupies `y` bytes, the stack pointer register is subtracted by `y` positions. Then `y` bytes will be occupied by `x`.

    * **`mov destination, source`**  
      Moves `source` content into `destination`. Don't be tricked by the command name. `source`'s content remains intact. This is a sort of copy command rather than a move command.

    * **`sub destination, source`**  
      `destination` will be equal to `destination - source`.

    * **`call function_address`**  
      This command calls a function by specifying its address in memory.

    * **`add destination, source`**  
      `destination` will be equal to `destination + source`.

    * **`leave`**  
      It does two things:
      1. `mov esp, ebp` -> discarding all local variables from the function.
      2. `pop ebp` -> restore the caller's base pointer.

    * **`ret`**  
      It takes the last 4 bytes from the stack and stores them inside `eip`.

    * **`xchg dest, src`**  
      Stands for exchange. It swaps the `src` operand with the `dest` operand. It's like doing three `mov` operations:
      1. Moving `dest` to a temporary space (another register).
      2. Moving `src` to `dest`.
      3. Moving the temporary register content to `src`.

    * **`nop`**  
      Stands for "no operation". It tells the CPU to literally do nothing and advance to the next instruction.

    ### Memory Alignment Note
    Data in memory is aligned when its address in memory is divisible by its dimension in bytes. A 4-byte integer is aligned in memory if its address is divisible by `4`. Aligned data is read by the CPU faster. 

    The same thing happens for functions. The CPU usually reads stuff in memory in chunks (usually 16 bytes). If a function occupies 37 bytes and the set alignment size is 16 bytes, it might add 11 bytes of `nop` instructions so that the next function starts at an address that is divisible by `16` (`48`).
 

## Sample Assembly Breakdown

**Objective:** Describing what the snippet does
**How it works:**: General view

# Second Binary

# Third Binary
