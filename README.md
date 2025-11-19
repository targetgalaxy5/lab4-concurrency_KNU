# Lab 4 — Concurrency / Synchronization
**Student:** Чубко Олег  
**Group:** К-26

Repository contains:
- `data_struct_demo.cpp` — C++17 program implementing the data structure with per-field `std::shared_mutex`, supports `read i`, `write i v`, `string` commands. Measures execution time (microseconds).
- `gen_commands.py` — generator for command files (variant, uniform, skewed).
- `data/` — generated command files for three scenarios (3 threads each).
- `results/` — template for results, screenshots and PDF report.
- `report.pdf` — full lab report (detailed, multi-page).

## How to run (short)
1. Compile C++ code:
```
g++ -std=c++17 -O2 data_struct_demo.cpp -lpthread -o demo
```
2. Generate command files (if you want to re-generate):
```
python3 gen_commands.py variant 1000 data/variant
python3 gen_commands.py uniform 1000 data/uniform
python3 gen_commands.py skewed 1000 data/skewed
```
3. Run (example):
```
./demo multi 3 data/variant_thread0.txt data/variant_thread1.txt data/variant_thread2.txt
```
4. Repeat each experiment 5 times and fill `results/table3x3.txt` with averages.

## Notes
- The program reads files into memory before timing, so file I/O isn't counted in measured time.
- `std::shared_mutex` is used per field to allow concurrent reads and exclusive writes.
- If your system does not have `std::shared_mutex` available, ensure you use a modern compiler (g++ 7+).
