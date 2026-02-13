# tad5212_breakout

A breakout board for TI's [TAD5212](https://www.ti.com/product/TAD5212) and [TAD5112](https://www.ti.com/product/TAD5112) DACs (they are drop-in replacements of each other).

Should work as both 2-layer and 4-layer boards. All signals are on layer 1.

If ordering the board with assembly, make sure the orientation of the tantalum caps is correct.

No guarantees on the level of noise, I am inexperienced in PCB design. Raise an issue if you have advice or ideas.

| ![Render of the PCB from the front](aud_f.png) | ![Render of the PCB from the back](aud_b.png) |
| ------------------- | --------------------- |

I test this board with the following configuration sequence:

```
delay(1000);
writeRegister(0x00, 0x00);  // PAGE_CFG
writeRegister(0x01, 0x01);  // SW_RESET
delay(10);
writeRegister(0x02, 0x01);  // DEV_MISC_CFG -- not in sleep
delay(10);
writeRegister(0x19, 0x40);  // ASI_CFG1
writeRegister(0x1a, 0x36);  // PASI_CFG0
writeRegister(0x64, 0x24);  // OUT1x_CFG0
writeRegister(0x65, 0x60);  // OUT1x_CFG2
writeRegister(0x66, 0x60);  // OUT1x_CFG2
writeRegister(0x76, 0x0c);  // CH_EN
writeRegister(0x78, 0x40);  // PWR_CFG
```
