<script src="processing.min.js"></script>
<canvas datasrc="haplotypes.pjs" width="600" height="450">`Can't load canvas object`</canvas>

Here, I'm showing the outcome of a basic demographic / mutational process, in which each circle represents a different genetic variant or [haplotype](http://en.wikipedia.org/wiki/Haplotype) within an evolving population.
Each time step, individuals from each haplotype are born or die according to a [Moran process](http://en.wikipedia.org/wiki/Moran_process), keeping the total population size constant.
Additionally, mutations enter the population, creating new haplotypes. This simulation is assuming haploid, rather than diploid, genetic structure; each individual possesses a single genotype.
		
Haplotypes are positioned according to a [force-directed algorithm](http://en.wikipedia.org/wiki/Force-directed_graph_drawing), where haplotypes act as charged particles and repel from all other haplotypes, and parent-and-child haplotypes are connected by idealized springs that keep them a certain distance apart.
In the resulting dynamics, there are usually a smaller number of high-frequency variants surrounding by their low-frequency mutational progeny. This behavior fits with [quasispecies models](href="http://en.wikipedia.org/wiki/Viral_quasispecies).
	
Stochastically, some haplotypes bear more offspring than other haplotypes, resulting in [genetic drift](href="http://en.wikipedia.org/wiki/Genetic_drift). 
Without mutation replenishing diversity, the population would eventually arrive at a single haplotype. 
With both genetic drift and mutation, the population reaches an equilibrium level of diversity. 
This diversity is often measured by the level of heterozygosity <i>H</i>, equal to the chance that two randomly selected individuals in the population share the same haplotype. 
The expected level of heterozygosity is equal to `\( \dfrac{\theta}{\theta+1} \)`, where <i>&theta;</i> is equal to the population-scaled mutation rate 2 <i>N &mu;</i> for haploid populations.  
This is two times the number of new mutations entering the population each generation.  
		
We can also measure diversity in terms of the total number of distinct haplotypes <i>k</i> in the population. 
The expected number of haplotypes can also be calculated from <i>&theta;</i> and is equal to `\( \sum_{i=1}^n \dfrac{\theta}{\theta+i-1} \)`. 
The visualization shows expected and observed heterozygosities and variant counts as the simulation proceeds. 
It's also possible to calculate the full distribution of the probability of observing <i>&eta;<sub>i</sub></i> individuals possessing haplotype <i>i</i>.  
This known as the [Ewen's sampling formula](href="http://en.wikipedia.org/wiki/Ewens's_sampling_formula).
		
These results represent the mutational corollary to the [genealogical process represented by the Kingman coalescent](/projects/coaltrace/).
		
Press <em>H</em> to bring up a listing of commands. 
