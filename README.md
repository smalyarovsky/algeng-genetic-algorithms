# Planetary System Generator

### The goal of the project is to generate synthetic planetary systems that are physically plausible and short-term dynamically stable. A genetic algorithm will optimize orbital and physical parameters of multiple planets orbiting a single star under astrophysical constraints.

## Dataset

Real multi-planet systems from open-source exoplanet catalogs (e.g., NASA Exoplanet Archive / Open Exoplanet Catalogue) will be used to obtain realistic parameter distributions (semi-major axes, eccentricities, inclinations, masses).

## Chromosome Description

Each individual represents a full star–planet system with N fixed planets.

For every planet, the chromosome contains the orbital and physical parameters:

$a$ — semi-major axis (AU)

$e$ — eccentricity

$i$ — inclination (degrees)

$\omega$ — argument of periapsis (degrees)

$\Omega$ — longitude of ascending node (degrees)

$M$ — initial mean anomaly (degrees)

$m$ — planet mass (Earth or Jupiter masses)

$R$ — planet radius (Earth or Jupiter radii)

The full chromosome is a flat vector of these values for all planets.

## Fitness Function

The fitness function evaluates each generated system using hard (mandatory) and soft (optimization) criteria.

### Hard Constraints

Non-crossing orbits

Basic Hill stability - orbital spacing must exceed a minimum multiple of the mutual Hill radius.

### Soft Metrics

Eccentricity realism - lower eccentricities are preferred; high values are penalized.

Regular orbital spacing - reward low variance in ratios $\frac{a_{i + 1}}{a_{i}}$ (geometric spacing).

System architecture quality - pefer systems with smooth outward increase in orbital periods and plausible mass–distance relationships.

Inclination moderation - small mutual inclinations are preferred for realism.

Habitability criterion (optional) - reward systems containing exactly one planet inside the classical habitable zone with approximately Earth-like radius and mass.

The final fitness score is a weighted sum of all soft metrics, with hard constraints enforced via large negative penalties.

## Desired Result

The genetic algorithm should converge to generating planetary systems that:

* obey short-term dynamical stability constraints

* contain non-intersecting and well-spaced orbits

* show realistic eccentricity, inclination, and mass distributions

* resemble the orbital structure of real observed multi-planet systems
