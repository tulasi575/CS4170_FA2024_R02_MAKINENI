## OpenMP Setup and Execution Guide

## Steps to Clone and Run the OpenMP Repository

1. **Open Terminal and SSH into OSC**

   ```sh
   ssh tulasi99@owens.osc.edu
   ```

   Replace `tulasi99` with your username. Enter your OSC account password and hit enter.

2. **Load Git Module**

   ```sh
   module load git
   ```

3. **Clone the Repository**

   ```sh
   git clone "https://github.com/CS-4170-5170-Fall-2024/OpenMP.git"
   ```

   If prompted, enter your GitHub username and password. If this method doesn't work, follow the next step.

4. **Generate GitHub Token**

   - Go to GitHub Tokens.
   - Click on **Generate new token (classic)**.
   - Select `repo` in the scopes and click on **Generate token**.

5. **Clone the Repository with Token**

   ```sh
   git clone "https://github.com/CS-4170-5170-Fall-2024/OpenMP.git"
   ```

   Use the generated token in place of your GitHub personal password.

6. **Navigate to the Cloned Repository**

   ```sh
   cd OpenMP
   ```

7. **Change Branch to "TrapRule3"**

   ```sh
   git checkout TrapRule3
   ```

8. **Load OpenMPI Module**

   ```sh
   module load openmpi
   ```

9. **Edit the Slurm Job Script**

   ```sh
   nano jobScript.slurm
   ```

   Replace `#SBATCH --account=PCS0288` . Save the file with `Ctrl+O` and exit with `Ctrl+X`.

10. **Submit the Slurm Job**

    ```sh
    sbatch jobScript.slurm
    ```

    The output will look like this:

    ```
    Submitted batch job 33428729
    ```

11. **Check the Output**
    ```sh
    cd Default
    cat results.csv
    ```
    The output will look like this:
    ```
    Serial Result: 912
    Serial Time: 0.0003
    Parallel Result: 912
    Parallel Time: 6.9e-05
    ```

## Performance Analysis

The following table shows the results of running the parallel trapezoidal rule program with varying numbers of threads, for an interval `[a=0, b=12]` and `n=99,999`. The table includes serial and parallel execution times, as well as calculated speedup and efficiency.

### Results Table

| Threads | Serial Time (s) | Parallel Time (s) | Speedup (S) | Efficiency (E) |
| ------- | --------------- | ----------------- | ----------- | -------------- |
| 1       | 0.000142        | 0.000103          | 1.38        | 1.38           |
| 2       | 0.000142        | 0.000103          | 1.38        | 0.69           |
| 3       | 0.000253        | 0.000161          | 1.57        | 0.52           |
| 4       | 0.000224        | 0.000203          | 1.10        | 0.28           |
| 5       | 0.000273        | 0.000158          | 1.73        | 0.35           |
| 6       | 0.000213        | 0.000164          | 1.30        | 0.22           |
| 7       | 0.000213        | 0.000164          | 1.30        | 0.19           |
| 8       | 0.000374        | 0.000148          | 2.53        | 0.32           |
| 9       | 0.000374        | 0.000148          | 2.53        | 0.28           |
| 10      | 0.000380        | 0.000225          | 1.69        | 0.17           |
| 11      | 0.000440        | 0.000168          | 2.62        | 0.24           |
| 12      | 0.000544        | 0.000217          | 2.51        | 0.21           |

### Speedup and Efficiency Calculations

**Speedup (S)** is calculated as:
\[ S = \frac{\text{Serial Time}}{\text{Parallel Time}} \]

**Efficiency (E)** is calculated as:
\[ E = \frac{S}{\text{Number of Threads}} \]
